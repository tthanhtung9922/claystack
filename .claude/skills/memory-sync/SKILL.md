---
name: memory-sync
description: >
  Scan session changes, extract lessons, and update the full memory system:
  CLAUDE.md hierarchy, .claude/rules, .claude/agents, .claude/skills, and
  4-type auto-memory. Trigger on /memory-sync, "sync memory", "update CLAUDE.md",
  or after a major feature session.
disable-model-invocation: true
allowed-tools:
  - Read
  - Write
  - Edit
  - Bash
  - Glob
  - Grep
---

# Memory Sync

The memory system has **two independent tiers**:

```
TIER 1 — Project memory (committed / local)
├── ./CLAUDE.md                          ← Monorepo root (always loaded)
├── <submodule-path>/CLAUDE.md           ← Per-submodule conventions
│                                          (auto-discovered via .gitmodules)
├── .claude/rules/<topic>.md             ← Path-scoped rules (glob frontmatter)
├── .claude/agents/<name>.md             ← Subagent definitions
├── .claude/skills/<name>/SKILL.md       ← User/Claude-invocable skills
└── CLAUDE.local.md                      ← Local only (gitignored)

TIER 2 — Auto-memory (cross-session, user-level)
└── $HOME/.claude/projects/<encoded-project-root>/memory/
    ├── MEMORY.md                        ← Index (≤200 lines, loaded every session)
    └── <topic>.md                       ← type: user | feedback | project | reference
```

---

## Step 0 — Derive runtime paths

Run this first. The result is used in every subsequent step — do not hardcode any path.

```bash
PROJECT_ROOT=$(git rev-parse --show-toplevel)
PROJECT_KEY=$(echo "$PROJECT_ROOT" | sed 's|:|-|g; s|[/\\]|-|g')
MEMORY_DIR="$HOME/.claude/projects/$PROJECT_KEY/memory"
echo "MEMORY_DIR=$MEMORY_DIR"
```

Use `$MEMORY_DIR` for all auto-memory operations below.

---

## Step 1 — Scan session changes

```bash
git diff HEAD~1 -- . \
  ':(exclude)*.lock' \
  ':(exclude)package-lock.json' \
  ':(exclude)*.snap' \
  ':(exclude)*.css.map'
git log --oneline --since="1 day ago"
```

> If no commits yet, use `git status` + `git diff`.

Identify and note:

| Change type | Examples |
|---|---|
| Libraries added / removed | package added, dependency dropped |
| Directory structure | new module, new routes |
| New conventions | naming patterns, component patterns |
| Important bugs encountered | SSR gotchas, env var issues |
| User decisions | chose A over B with explicit reason |
| Automation changes | new skill, agent, or hook |

---

## Step 2 — Inventory the full system

**2a. CLAUDE.md hierarchy — auto-discover via `.gitmodules`**

Never hardcode the submodule list. Extract it dynamically:

```bash
git config --file .gitmodules --get-regexp '^submodule\..*\.path$' \
  | awk '{print $2}' \
  | sort
# Fallback if .gitmodules is absent but submodules are initialized:
# git submodule status | awk '{print $2}'
```

For each path returned, check `<path>/CLAUDE.md`:

```bash
while read -r sub; do
  f="$sub/CLAUDE.md"
  [ -f "$f" ] && echo "FOUND  $f" || echo "MISS   $f"
done < <(git config --file .gitmodules --get-regexp '^submodule\..*\.path$' | awk '{print $2}')
```

Also include root `./CLAUDE.md`. Read each file found. Note:
- Content that is stale relative to Step 1
- Submodules missing a `CLAUDE.md` (MISS) — decide if one is needed

> **Submodule note**: A `CLAUDE.md` inside a submodule belongs to that repo.
> To edit it, commit inside the submodule first, then bump the pointer in the monorepo.

**2b. Rule files**

```bash
ls .claude/rules/ 2>/dev/null
```

Read each file. Check the `paths:` frontmatter field — this is the activation scope. Rules without `paths:` consume tokens every session.

**2c. Agents and Skills**

```bash
ls .claude/agents/ 2>/dev/null
ls .claude/skills/ 2>/dev/null
```

Check the frontmatter description of each file. If any agent/skill was added or modified this session, flag it for the Step 6 report.

**2d. Auto-memory index**

```bash
cat "$MEMORY_DIR/MEMORY.md"
```

Read each memory file listed in the index.

---

## Step 3 — Remove stale content

Compare against Step 1 results. Remove/fix before adding.

### 3a. Root `./CLAUDE.md`

| Staleness signal | Action |
|---|---|
| Library no longer in `package.json` | Remove |
| Build/test commands changed | Update to match reality |
| Directory path no longer exists | Remove or fix |
| `@reference` points to missing file | Remove ref or create file |
| Architecture diagram is outdated | Update |
| Over 200 lines | Move details to `.claude/rules/`, replace with `@ref` |

### 3b. Submodule `CLAUDE.md` files (applies to ALL submodules)

Iterate the submodule list from Step 2a. For each existing `<path>/CLAUDE.md`, apply this checklist:

| Staleness signal | Action |
|---|---|
| Package/dependency version doesn't match the submodule's own manifest (`package.json`, `*.csproj`, etc.) | Update to match manifest |
| Convention changed in code (naming, file layout, handler structure) | Rewrite the relevant section |
| Build/test/lint commands no longer work | Update to match scripts / build targets |
| Content duplicated from root `./CLAUDE.md` | Remove — keep only what differs from root |
| Points to a file or module that no longer exists | Remove or fix |
| Over 200 lines | Split to a separate doc + `@ref` |

**Principle**: a `<submodule>/CLAUDE.md` should only contain conventions specific to that repo. Anything shared with root must be removed.

> When editing: commit inside the submodule first, then bump the monorepo pointer in a separate commit.

### 3c. Rule files (`.claude/rules/*.md`)

- `paths:` glob no longer matches real structure → update
- Library referenced in rule is no longer used → remove
- Duplicate content across rules → merge
- Rule has no `paths:` and isn't broadly applicable → add `paths:` or delete

### 3d. Auto-memory files

```bash
ls "$MEMORY_DIR/"
```

For each file:
- **project** memories: is the state still accurate? (e.g., if a tool was uninstalled, update the relevant file)
- **feedback** memories: still applicable → keep
- **user** memories: still accurate → keep
- Irrelevant memories → delete file and remove its entry from `MEMORY.md`

---

## Step 4 — Add new content

### Routing table

| Content type | Destination |
|---|---|
| Monorepo-wide build/test/lint commands | `./CLAUDE.md` |
| Overall architecture, dev tools, MCP servers | `./CLAUDE.md` |
| Convention specific to one submodule | `<submodule-path>/CLAUDE.md` (path from Step 2a) |
| Rules for a specific file type (`*.tsx`, `*.cs`) | `.claude/rules/<topic>.md` |
| Local URLs, endpoints, machine-specific config | `CLAUDE.local.md` |
| Important bug or gotcha | Auto-memory `feedback_*.md` (type: feedback) |
| User decision (chose A over B) | Auto-memory `feedback_*.md` (type: feedback) |
| Feature progress or section status | Auto-memory `project_*.md` (type: project) |
| User habits or preferences | Auto-memory `user_*.md` (type: user) |
| Pointer to an external system | Auto-memory `reference_*.md` (type: reference) |

### CLAUDE.md update format (WHY-WHAT-HOW)

```markdown
## <Convention Name>

**WHY**: <reason — constraint, incident, or trade-off>
**WHAT**: <the specific rule>
**HOW**: <example — code snippet or command>
```

### Auto-memory file format

```markdown
---
name: <short name>
description: <one line — used to judge relevance when loading>
type: user | feedback | project | reference
---

<content>

**Why:** <origin or reason>
**How to apply:** <when/how to use this information>
```

**MEMORY.md index rules:**
- One entry per line, under 150 characters: `- [Title](file.md) — one-line hook`
- Never write memory content directly into `MEMORY.md`
- Remove the entry immediately when deleting a file
- Keep total ≤ 200 lines

**When TO create a new memory:**
- Important bug or gotcha encountered for the first time
- User corrected Claude's approach ("no, don't do that" / "yes, exactly, keep doing that")
- Architectural decision with a trade-off (chose X over Y)
- Feature status changed (new tool is live)

**When NOT to create a memory:**
- Pattern already exists in CLAUDE.md or in the code
- Implementation details (use `git log` instead)
- Temporary context from the current session

### Creating a new rule file

```markdown
---
description: <when this activates>
paths:
  - "src/**/*.tsx"
  - "src/**/*.ts"
---

# <Rule Name>

...
```

---

## Step 5 — Size check

Retrieve the submodule list from Step 2a, then measure all CLAUDE.md files:

```bash
{ echo ./CLAUDE.md; \
  git config --file .gitmodules --get-regexp '^submodule\..*\.path$' \
    | awk '{print $2 "/CLAUDE.md"}'; } \
  | xargs -r -I{} sh -c '[ -f "{}" ] && wc -l "{}"'

wc -l .claude/rules/*.md 2>/dev/null
wc -l "$MEMORY_DIR/MEMORY.md"
```

| File | Limit |
|---|---|
| `./CLAUDE.md` | < 200 lines |
| Each `<submodule>/CLAUDE.md` | < 200 lines |
| Each rule file | < 80 lines |
| `MEMORY.md` | ≤ 200 lines |
| Each memory file | No hard limit — keep concise |

---

## Step 6 — Report

Print results for every `CLAUDE.md` discovered in Step 2a (root + each submodule from `.gitmodules`).

```
─────────────────────────────────────────────────────────────
MEMORY SYNC — Results
─────────────────────────────────────────────────────────────
CLAUDE.md hierarchy              (<total> files, <M> submodules)
  [ok] ./CLAUDE.md                          — <changed | unchanged>
  <iterate submodules from Step 2a>
  [ok] <submodule-path-1>/CLAUDE.md         — <changed | unchanged>
  [ok] <submodule-path-2>/CLAUDE.md         — <changed | unchanged>
  [!]  <submodule-path-3>/CLAUDE.md         — MISS (no file; decide if needed)
  [-]  <submodule-path-4>                   — skipped (submodule not initialized)

Rules / Agents / Skills
  [ok] .claude/rules/<name>.md              — <changed | unchanged>
  [--] .claude/agents/<name>.md             — exists, unchanged
  [--] .claude/skills/<name>/SKILL.md       — exists, unchanged

Auto-memory
  [+]  ADDED:    <file>.md                  — <reason>
  [~]  UPDATED:  <file>.md                  — <reason>
  [x]  REMOVED:  <file>.md                  — no longer relevant
  [sz] MEMORY.md: <N> / 200 lines

Size
  ./CLAUDE.md                        : <N> / 200 lines
  <submodule-path-1>/CLAUDE.md       : <N> / 200 lines
  rules/*.md                         : <N> files, max <M> lines
─────────────────────────────────────────────────────────────
```

**Rendering rules:**
- List submodules in the order they appear in `.gitmodules`.
- Always show every submodule — including MISS and skipped — so the reader knows the full list was checked.
- If there are no submodules (flat repo), omit submodule lines entirely; only print `./CLAUDE.md`.
- If nothing changed: `All memory tiers are in sync.`

---

## Important notes

- Only add information confirmed by the diff or actual code — never speculate
- No duplication between CLAUDE.md and auto-memory — route to exactly one destination per the routing table
- Rule files without `paths:` consume tokens every session — always add a glob
- Auto-memory path is always derived at runtime via Step 0 — never hardcode it
- `MEMORY.md` is an index only — never write memory content directly into it
