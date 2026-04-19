# AGENTS.md Templates

## Key Principles

- **Concise**: dense, high-signal instructions
- **Actionable**: commands and paths should be executable
- **Project-specific**: capture local patterns, not universal advice
- **Current**: reflect the repository as it exists today
- **Scoped**: match guidance to the directory where the file lives

---

## Recommended Sections

Use only the sections relevant to the project.

### Commands

```markdown
## Commands

| Command | Purpose |
|---------|---------|
| `<install command>` | Install dependencies |
| `<dev command>` | Start local development |
| `<test command>` | Run the relevant test suite |
| `<lint command>` | Lint or format |
```

### Architecture

````markdown
## Architecture

```
<root>/
  <dir>/    # <purpose>
  <dir>/    # <purpose>
  <file>    # <why it matters>
```
````

### Workflow

```markdown
## Workflow

- For `<task>`, start in `<path>`
- Update `<file>` when changing `<area>`
- Run `<command>` before handing off
```

### Constraints

```markdown
## Constraints

- Preserve `<public contract>`
- Ask before changing `<risky area>`
- Keep `<generated file>` in sync with `<source>`
```

### Validation

```markdown
## Validation

- `<command>` — fast local validation
- `<command>` — full verification
- If `<condition>`, also check `<path or command>`
```

### Gotchas

```markdown
## Gotchas

- `<non-obvious rule>`
- `<ordering dependency>`
- `<common failure mode>`
```

---

## Template: Project Root (Minimal)

````markdown
# <Project Name>

<One-line description for the agent>

## Commands

| Command | Purpose |
|---------|---------|
| `<command>` | <description> |

## Architecture

```
<structure>
```

## Gotchas

- <gotcha>
````

---

## Template: Project Root (Comprehensive)

````markdown
# <Project Name>

<One-line description for the agent>

## Commands

| Command | Purpose |
|---------|---------|
| `<command>` | <description> |

## Architecture

```
<structure with descriptions>
```

## Workflow

- <preferred approach>

## Constraints

- <important guardrail>

## Validation

- `<command>` - <scope>

## Gotchas

- <non-obvious pattern>
````

---

## Template: Monorepo Root

```markdown
# <Monorepo Name>

<Description>

## Packages

| Package | Purpose | Path |
|---------|---------|------|
| `<name>` | <purpose> | `<path>` |

## Commands

| Command | Purpose |
|---------|---------|
| `<command>` | <description> |

## Cross-Package Rules

- <shared pattern>
- <sync or generation rule>
```

---

## Template: Package or Module

```markdown
# <Package Name>

<Purpose of this scope>

## Commands

| Command | Purpose |
|---------|---------|
| `<command>` | <description> |

## Local Workflow

- <where to start>
- <what to update together>

## Constraints

- <package-specific guardrail>

## Gotchas

- <package-specific quirk>
```

---

## Update Principles

When updating any `AGENTS.md`:

1. Use real paths and commands from the repository.
2. Keep each line useful to a future agent session.
3. Put shared guidance at the highest sensible scope.
4. Put local exceptions close to the code they govern.
5. Remove duplicated text when a parent file already covers it.
