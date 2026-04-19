# AGENTS.md Update Guidelines

## Core Principle

Only add information that will materially improve future agent sessions. Instruction space is limited, so every line must earn its place.

## What TO Add

### 1. Commands and Validation Steps

```markdown
## Commands

`pnpm test --filter api` - Run the API package tests
`pnpm lint` - Repository-wide lint pass
```

Why: saves future sessions from rediscovering the working command set.

### 2. Project-Specific Workflows

```markdown
## Workflow

- Regenerate `src/generated/` with `pnpm codegen` after schema changes
- Update both `server/routes.ts` and `client/api.ts` when adding endpoints
```

Why: captures multi-file habits that are easy to miss.

### 3. High-Value Constraints

```markdown
## Constraints

- Preserve `v1` API response fields; mobile clients still depend on them
- Ask before editing `infra/terraform/production`
```

Why: reduces risky edits in sensitive areas.

### 4. Non-Obvious Patterns and Gotchas

```markdown
## Gotchas

- Tests must run serially because they share a seeded database
- `pnpm dev` expects `.env.local` copied from `.env.example`
```

Why: prevents repeated debugging.

### 5. Scoped Guidance

```markdown
## Architecture

`packages/web/AGENTS.md` covers frontend-only rules.
`packages/api/AGENTS.md` covers backend-only validation and contracts.
```

Why: helps the agent choose the right instruction layer.

## What NOT to Add

### 1. Generic Agent Advice

Bad:
```markdown
Think carefully before editing files.
Write clean code.
```

These lines add little project value.

### 2. Obvious Code Facts

Bad:
```markdown
The `UserService` class handles user logic.
```

The code already tells us this.

### 3. One-Off Incident Notes

Bad:
```markdown
A bug in March 2025 caused the button color to break.
```

This ages quickly and clutters the file.

### 4. Long Tutorials

Bad:
```markdown
PostgreSQL is a relational database system that ...
```

Prefer terse, local guidance tied to the project.

### 5. Unverified Harness Claims

Bad:
```markdown
The harness always merges this file after user config.
```

Only document precedence or discovery rules after verification.

## Diff Format for Updates

For each suggested change:

### 1. Identify the File and Scope

```text
File: ./AGENTS.md
Section: Validation (new section after ## Workflow)
```

### 2. Show the Change

```diff
 ## Workflow
 ...
 
+## Validation
+
+- `pnpm lint` - repository-wide lint
+- `pnpm test --filter web` - web package tests
```

### 3. Explain Why

> **Why this helps:** Validation steps were missing, so future sessions would need to inspect package scripts before verifying changes.

## Validation Checklist

Before finalizing an update, verify:

- [ ] Each addition is project-specific
- [ ] Commands and paths are real
- [ ] Guidance is placed at the right scope
- [ ] Nested files do not conflict with parent files
- [ ] Harness-specific claims are verified
- [ ] The wording is concise and actionable
