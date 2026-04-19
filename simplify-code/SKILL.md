---
name: simplify-code
description: Simplifies existing code while preserving behavior, tests, and public contracts. Use when the user asks to simplify, refactor, clean up, reduce complexity, improve readability, remove duplication, or polish recently changed code without changing features.
---

# Simplify Code

## Quick start

Target the files named by the user or the code touched in the current task. Make the smallest set of edits that improves readability and maintainability while keeping behavior, APIs, and data contracts stable.

## Workflow

1. Set scope
   - Start with explicitly requested files.
   - Otherwise focus on code modified in the current session.
   - Expand to nearby code only when the simplification crosses file or function boundaries.

2. Find safe simplifications
   - Flatten unnecessary nesting with guard clauses.
   - Replace dense expressions with explicit control flow.
   - Remove duplication, dead branches, and needless indirection.
   - Extract helpers when they give a clearer unit of meaning.
   - Improve names when the new names are more precise.

3. Follow project conventions
   - Apply guidance from AGENTS.md and local file patterns.
   - Keep imports, types, and component structure consistent with the codebase.
   - Prefer readable, explicit code over clever compression.
   - Use `if`/`switch` instead of nested ternaries for multi-branch logic.

4. Preserve behavior
   - Keep runtime behavior, side effects, error semantics, and external interfaces stable.
   - Keep business rules, validation, telemetry, and meaningful comments intact.
   - Treat public APIs, persistence formats, and wire contracts as behavior-sensitive.

5. Verify the change
   - Check imports, types, call sites, and obvious edge cases.
   - Add or update tests when the simplification changes control flow in behavior-sensitive areas.
   - Surface any uncertainty before making broad or risky refactors.

## Guardrails

- Prefer incremental edits that are easy to review.
- Keep unrelated churn out of the diff.
- Avoid style-only rewrites across large areas unless the user asks for broad cleanup.
- Document only changes that affect understanding or review.

## Output

When reporting back, include:
- files changed
- the main simplifications
- any areas that deserve tests or manual verification
