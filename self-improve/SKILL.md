---
name: self-improve
description: Audits and improves AGENTS.md files in repository. Use when the user asks to check, audit, update, improve, or fix AGENTS.md files, repository guidance for coding agents, agent instructions, or project memory. Scans for AGENTS.md files, evaluates quality against concise rubrics, outputs a quality report, then applies targeted updates after approval.
---

# Self Improve

Audit, evaluate, and improve AGENTS.md files so the active agent harness gets accurate, high-signal project context.

**This skill can write to AGENTS.md files.** Always present the quality report before editing, then wait for user approval.

## Quick start

1. Discover candidate files:
   ```bash
   find . -name "AGENTS.md" 2>/dev/null | head -50
   ```
2. Read each file completely and cross-check it against the repository.
3. Score each file with [references/quality-criteria.md](references/quality-criteria.md).
4. Output an `AGENTS.md Quality Report` with issues and proposed additions.
5. After approval, apply the smallest useful edits.

## Scope

Common locations:
- `./AGENTS.md` — shared project instructions
- `./packages/*/AGENTS.md` — package or module instructions
- nested `AGENTS.md` files — feature or directory-specific guidance

Harnesses differ in discovery rules and precedence. When the target harness is known, align recommendations with its docs and verify how parent and child `AGENTS.md` files combine.

## Workflow

### 1. Discovery
- Find every `AGENTS.md` in the repository.
- Group files by scope: root, package, nested.
- Flag duplicate, conflicting, or stale instructions.

### 2. Assessment
- Check commands, workflows, constraints, architecture, and gotchas.
- Verify referenced paths, scripts, and tools against the repo.
- Score each file and assign a grade.

### 3. Report
Always output the report before editing.

```md
## AGENTS.md Quality Report

### Summary
- Files found: X
- Average score: X/100
- Files needing update: X

### File-by-File Assessment
...
```

Include:
- per-file scores
- specific issues
- recommended additions
- cross-file conflicts

### 4. Update design
Use [references/update-guidelines.md](references/update-guidelines.md).
Prefer:
- copy-paste ready commands
- project-specific workflows
- high-value constraints
- non-obvious patterns
- crisp directory guidance

### 5. Apply changes
- Ask for confirmation.
- Preserve structure, tone, and scope of each file.
- Make the smallest reviewable edit set.
- Show diffs or quoted additions before applying when helpful.

## Templates

Use [references/templates.md](references/templates.md) for root, monorepo, and module layouts.

## Guardrails

- Keep content dense, current, and project-specific.
- Remove or rewrite stale, generic, or duplicated guidance.
- Avoid harness-specific claims unless verified.
- Keep shared instructions in `AGENTS.md`; keep user-local preferences in harness-local config when supported.
