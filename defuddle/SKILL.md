---
name: defuddle
description: Extracts clean readable content and metadata from web pages with the Defuddle CLI. Use for reading, transforming, or inspecting content from a URL or local HTML file.
---

# Defuddle

## Quick start

Use the Defuddle CLI through `npx` for one-off extraction.

```bash
npx --yes defuddle parse https://example.com/article --markdown
```

Use `--json` when downstream steps need structured fields.

```bash
npx --yes defuddle parse https://example.com/article --json
```

## Workflow

1. Pick the smallest output that fits the task.
   - Readable article text: `--markdown`
   - Structured metadata plus content: `--json`
   - Single field such as `title`: `--property title`
   - Clean HTML for further processing: omit format flags

2. Run Defuddle on a URL or local HTML file.

```bash
npx --yes defuddle parse <url-or-file> [--markdown|--json|--property <name>] [-o output-file]
```

3. Save large output to a file when it will be reused.

```bash
npx --yes defuddle parse <url> --markdown -o article.md
```

4. Inspect extraction details when quality needs verification.

```bash
npx --yes defuddle parse <url> --json --debug
```

## Guardrails

- Treat this skill as a foundational web-reading capability for public pages that Defuddle can parse directly.
- Prefer `npx --yes defuddle` for ad hoc use.
- Prefer `--markdown` for summarization, note-taking, LLM input, and documentation reading.
- Prefer `--json` when title, author, domain, publish date, or word count matter.
- Use `--property` for a single value to reduce output volume.
- Use `-o` for long pages to avoid terminal truncation.
- Pass `-l <language>` when page language affects the result.

## Common properties

Useful property names include `content`, `title`, `description`, `author`, `site`, `domain`, `language`, `published`, `wordCount`, and `image`.

See [REFERENCE.md](REFERENCE.md) for command patterns, output fields, and extraction tips.
