# Code Quality Skill

## Purpose

Review real code changes like a staff engineer, using the project's own quality commands and standards.

## When to Use

Use after implementation and before commit, merge, or release. Also use when inheriting unreviewed code changes.

## Inputs Expected

- Change goal or ticket
- Changed files or diff
- Allowed and forbidden files
- Project docs and agent instructions
- Any known test or build constraints

## Discover Project-specific Quality Commands

Discover commands from real project files before running anything:

- `package.json`
- `pyproject.toml`
- `requirements.txt`
- `Makefile`
- `.github/workflows/`
- `README.md`
- `AGENTS.md`
- `CLAUDE.md`
- `CODEX.md`

Do not invent commands. If commands are absent or ambiguous, report that instead of guessing.

## Required Checks

- Type checking
- Linting
- Formatting
- Unit tests
- Integration tests if available
- Build verification
- Changed-file review
- Dead code
- Unused imports
- Duplicated logic
- Error handling
- Logging quality
- Security-sensitive changes
- Performance-sensitive changes
- Unrelated edits
- Test coverage gaps
- Documentation drift

## Output Format

- Commands discovered
- Commands run
- Results
- Code issues found
- Test gaps
- Risk level
- Required fixes
- Ship recommendation

## Stop Conditions

Stop and report when:

- No quality commands are found
- Tests cannot run
- Build fails
- Scope is unclear
- Security-sensitive change lacks review
