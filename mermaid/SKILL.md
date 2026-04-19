---
name: mermaid
description: Creates, repairs, and validates Mermaid diagrams with the official Mermaid CLI and a local validation script. Use when working with Mermaid code blocks, `.mmd` files, flowcharts, sequence diagrams, ER diagrams, state diagrams, or when a user asks to fix Mermaid syntax or rendering issues in Markdown or docs.
---

# Mermaid Skill

Create or edit Mermaid diagrams in a form that can be validated locally before shipping them into documentation.

## Quick start

1. Put the diagram in a standalone file such as `diagram.mmd`.
2. Validate and render it:
   ```bash
   ./scripts/validate.sh diagram.mmd [output.svg]
   ```
3. Fix any errors reported by the CLI.
4. Copy the validated Mermaid source into the target Markdown file when needed.

## When to use this skill

- Writing a new Mermaid diagram.
- Repairing Mermaid syntax or rendering failures.
- Extracting a Mermaid block from Markdown into `*.mmd` for validation.
- Producing an SVG artifact for review.

## Workflows

### New or updated diagram

1. Draft the diagram as plain Mermaid in `*.mmd`.
2. Keep node IDs stable while iterating.
3. Run `./scripts/validate.sh diagram.mmd`.
4. Review the CLI result, rendered output, and ASCII preview when available.
5. Apply fixes until validation passes.
6. Embed the final Mermaid block back into Markdown or docs.

### Diagram already embedded in Markdown

1. Extract the Mermaid block into `diagram.mmd`.
2. Validate it with `./scripts/validate.sh diagram.mmd`.
3. Copy the validated source back into the Markdown file.

## Validation behavior

- Uses `@mermaid-js/mermaid-cli` to parse and render the diagram.
- Writes to a temporary SVG when no output path is provided.
- Prints a best-effort ASCII preview via `beautiful-mermaid`.
- Returns a non-zero exit code on syntax or rendering failure.

## Environment notes

- Requires `node` and `npx`.
- First run may download Chromium through Puppeteer.
- Set `PUPPETEER_EXECUTABLE_PATH` when the environment needs an explicit browser path.

## Guardrails

- Validate plain Mermaid files; extract Mermaid blocks from Markdown first.
- Treat the ASCII preview as a convenience check and use the rendered SVG as the source of truth.
- Prefer small diagram edits and re-run validation after each meaningful change.
