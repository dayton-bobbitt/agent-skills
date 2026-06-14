---
name: pensieve
description: Scans project-specific memories across ~/.claude/projects, identifies ones that should apply globally (communication preferences, coding workflows, behavioral patterns), and promotes them to ~/AGENTS.md. Use when you want to distill cross-project learnings into a global instruction set, or when AGENTS.md feels stale or incomplete.
---

# Pensieve

Promote project-scoped memories to global instructions in `~/AGENTS.md`.

## Flags

- `--all` — include `project` and `reference` type memories in addition to the default `user` and `feedback` types

## Phase 1 — Scan

Read every project under `~/.claude/projects/`:

1. For each project, locate `memory/MEMORY.md` and follow its links to individual memory files
2. Read each memory file's frontmatter
3. Skip files with `promoted: true` in frontmatter
4. Filter by type: default = `user` + `feedback`; with `--all` = all types

Report before proceeding: "Found N memories across M projects (K already promoted). Evaluating X as candidates."

## Phase 2 — Classify

Read the full content of each candidate memory. Classify each as:

- **Global:** a behavioral rule, communication preference, or workflow pattern not tied to a specific project, repository, or technology stack
- **Project-specific:** depends on a particular repo, codebase, team, deadline, or toolchain

Cross-project duplicates (same rule appearing in multiple projects) are the strongest signal for promotion — weight them heavily toward global.

Present the global candidates as a numbered list, one line each. Then offer: "I filtered out N memories as project-specific. Would you like to review them?"

## Phase 3 — User Confirmation

Wait for the user to approve, reject, or adjust the candidate list. If they ask to see filtered memories, show them and allow additions to the promotion set before proceeding.

## Phase 4 — Synthesize

With the approved set:

1. Read `~/AGENTS.md` in full to understand existing sections and content
2. Group approved memories by theme
3. For each group: write concise, succinct bullets, merging near-duplicates into a single sharper rule — do not repeat the same instruction twice
4. Slot synthesized rules into existing sections where they fit; create new section headings where no existing section applies
5. Show a preview of only the new or changed content (not the full file)

Section headings should emerge from the content, not from a fixed taxonomy. Use the user's own vocabulary where possible.

## Phase 5 — Write and Mark

On user confirmation of the preview:

1. Write the synthesized additions to `~/AGENTS.md`
2. For each promoted source memory file, add `promoted: true` to the YAML frontmatter block

Do not delete source memory files. They serve as the audit trail with full Why/How to apply content.
