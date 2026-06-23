# Read-only Review Lane

## Purpose

Inspect code, docs, or plans and return findings without editing files.

## Allowed Actions

- Read files
- Search code
- Run safe read-only commands
- Summarize risks
- Recommend next steps

## Forbidden Actions

- Editing files
- Installing tools
- Running destructive commands
- Changing configuration
- Committing changes

## Inputs

- Review goal
- Allowed paths
- Forbidden paths
- Expected report format

## Outputs

- Findings by severity
- Evidence with file paths
- Suggested fixes
- Open questions

## Stop Conditions

Stop if the review requires file edits, sensitive access, or destructive commands.
