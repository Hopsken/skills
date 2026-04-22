# Defuddle Reference

## Installation modes

Use one of these command styles:

```bash
# One-off use
npx --yes defuddle parse <source>

# Global install
npm install -g defuddle
defuddle parse <source>
```

`<source>` can be a URL or a local HTML file.

## Common command patterns

### Extract a URL as Markdown

```bash
npx --yes defuddle parse https://example.com/article --markdown
```

### Extract a URL as JSON

```bash
npx --yes defuddle parse https://example.com/article --json
```

### Extract a single property

```bash
npx --yes defuddle parse https://example.com/article --property title
npx --yes defuddle parse https://example.com/article --property author
npx --yes defuddle parse https://example.com/article --property content
```

### Parse a local HTML file

```bash
npx --yes defuddle parse page.html --markdown
```

### Save output to a file

```bash
npx --yes defuddle parse https://example.com/article --markdown --output article.md
npx --yes defuddle parse https://example.com/article --json --output article.json
```

### Prefer a language

```bash
npx --yes defuddle parse https://example.com/article --json --lang en
```

### Enable debug mode

```bash
npx --yes defuddle parse https://example.com/article --json --debug
```

## Output mode guide

- Default output: cleaned HTML in stdout
- `--markdown` or `--md`: main content converted to Markdown
- `--json`: structured metadata plus content
- `--property <name>`: one top-level field only
- `--output <file>`: write results to disk
- `--lang <code>`: request a preferred language for multilingual pages
- `--debug`: include extraction diagnostics

## Useful JSON fields

Common fields returned by `--json` include:

- `content`
- `contentMarkdown`
- `title`
- `description`
- `author`
- `site`
- `domain`
- `favicon`
- `image`
- `language`
- `published`
- `wordCount`
- `parseTime`
- `extractorType`
- `debug`

## Extraction tips

- Use Markdown when the next step is summarization, note capture, or LLM ingestion.
- Use JSON when metadata will drive filtering, routing, or storage.
- Use a single property when the task needs one value such as `title` or `author`.
- Use `--output` for long articles and pages with large bodies.
- For pages that require browser rendering or authentication, capture the rendered HTML first and parse the saved file.

## CLI scope

This skill focuses on the Defuddle CLI. Advanced parser options such as custom DOM handling belong to the Node.js API documented at https://defuddle.md/docs.
