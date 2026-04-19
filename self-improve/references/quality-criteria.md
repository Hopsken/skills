# AGENTS.md Quality Criteria

## Scoring Rubric

### 1. Commands and Workflows (20 points)

**20 points**: Essential commands and operating flows are documented with context
- setup, dev, build, test, lint, deploy, or review commands are present where relevant
- common agent tasks are mapped to concrete commands or files
- validation steps are clear

**15 points**: Most commands present, some missing context or coverage

**10 points**: Basic commands only, little workflow guidance

**5 points**: Few commands, many gaps

**0 points**: No commands or workflows documented

### 2. Scope and Architecture (20 points)

**20 points**: Clear map of the codebase and instruction boundaries
- key directories or packages are explained
- ownership or purpose of major areas is clear
- nested `AGENTS.md` scopes make sense
- entry points or key config files are identified

**15 points**: Good overview with minor gaps

**10 points**: Basic directory listing only

**5 points**: Vague or incomplete

**0 points**: No useful structure or scope info

### 3. Constraints and Guardrails (15 points)

**15 points**: Important operating constraints are explicit
- risky areas are called out
- public APIs, data contracts, migrations, or release-sensitive paths are identified
- review expectations or approval boundaries are clear

**10 points**: Some constraints documented

**5 points**: Minimal constraints or mixed signal

**0 points**: No practical guardrails

### 4. Non-Obvious Patterns and Gotchas (15 points)

**15 points**: Important quirks and local conventions are captured
- unusual workflows are explained
- ordering dependencies or environment quirks are documented
- "why this exists" is present for surprising patterns

**10 points**: Some patterns documented

**5 points**: Minimal pattern coverage

**0 points**: No patterns or gotchas

### 5. Currency and Accuracy (15 points)

**15 points**: Reflects the current repository state
- commands still work
- file references are valid
- stack and tooling are current
- stale instructions were cleaned up

**10 points**: Mostly current, minor staleness

**5 points**: Several outdated references

**0 points**: Severely outdated or misleading

### 6. Conciseness and Actionability (15 points)

**15 points**: Dense, precise, and executable
- each section helps future agent sessions
- commands can be copied directly
- phrasing is specific and short
- generic process advice is excluded

**10 points**: Mostly concise and actionable

**5 points**: Verbose or partly vague

**0 points**: Filler-heavy or theoretical

## Assessment Process

1. Read each `AGENTS.md` file completely.
2. Cross-reference it with the repository:
   - check referenced files and directories
   - inspect scripts and task runners
   - verify workflows against actual project structure
3. Verify harness-specific claims when they appear.
4. Score each criterion.
5. Calculate total and assign a grade.
6. List concrete issues and targeted improvements.

## Red Flags

- commands that would fail
- references to deleted files or renamed packages
- generic agent advice with little project value
- conflicting instructions across nested `AGENTS.md` files
- duplicated policy copied from templates without customization
- outdated workflow steps after toolchain or architecture changes
- scope rules that are ambiguous for multi-package repositories
