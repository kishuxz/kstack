# Review Skill

## Purpose

Perform a staff-engineer review of a completed change.

## When to Use

Use before commit, merge, or release.

## Inputs Expected

- Original goal
- Diff or changed files
- Test results
- Allowed and forbidden files

## Process

1. Compare diff to scope.
2. Review correctness and edge cases.
3. Check hidden behavior changes.
4. Check type, test, and security risk.
5. Identify overengineering and unrelated edits.
6. Recommend ship, revise, or block.

## Required Checks

- Correctness
- Edge cases
- Hidden behavior changes
- Type errors
- Test gaps
- Security-sensitive changes
- Overengineering
- Unrelated edits

## Output Format

- Blockers
- Non-blocking issues
- Suggested fixes
- Verification needed
- Ship recommendation

## Stop Conditions

Stop after review. Do not fix issues unless asked.
