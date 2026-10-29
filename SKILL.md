---
name: commit-rules
description: Commit message rules (Conventional Commits, English, short list-style body). Use when creating a git commit, or writing or editing a commit message or PR description.
---

# Commit message rules

Commit messages follow [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/). Messages and PR descriptions are written in English.

## Workflow

Do not ask for a description of the changes. Build the message from the repository state.

1. Inspect the changes (read-only):
   - `git branch --show-current`
   - `git status --short`
   - `git diff HEAD --stat` to gauge the size; for large diffs read only the key files
   - `git diff HEAD`
   - `git log -5 --oneline`
2. If there are staged changes, use only them; otherwise use all changes to tracked files. Ignore untracked service files unless they are the point of the change.
3. The branch name (`<type>/<task-id>-<description>`) is only a hint for `type` and `scope`. If it contradicts the diff, trust the diff. Do not put the branch name or task number into the message.
4. Take `scope` from the affected module or component, using project terminology and the style of recent commits. Do not use file names. If the changes span several independent components, omit the scope.
5. Group changes by meaning, not by file.
6. Show the message in a `text` block and stop.

## Format

```text
<type>(<scope>)[!]: <short description>

- <action> <change> (<reason>)
- <action> <change> (<reason>)

Note: <required action>
```

- Header: imperative mood, short, describes the result rather than the process.
- Add a body only when the header is not enough. Separate it with a blank line.
- One body line per logical change. Do not list files, repeat the header or write long paragraphs.
- Actions: `add`, `fix`, `update`, `remove`, `refactor`, `improve`, `optimize`.
- Give a reason in parentheses only when it helps to understand the change.
- Include only what is confirmed by the actual changes.

## Types

| Type | Purpose |
| --- | --- |
| `feat` | new functionality |
| `fix` | bug fix |
| `docs` | documentation |
| `refactor` | refactoring without behavior change |
| `perf` | performance |
| `test` | tests |
| `build` | build and dependencies |
| `ci` | CI/CD |
| `chore` | technical and housekeeping changes |
| `style` | formatting without logic change |

Choose the type by the content of the changes. Other types are fine if the project uses them.

## Manual steps

If actions are needed after deployment, add a final line `Note: <what to do and what happens if skipped>`. Otherwise omit `Note:`.

## Breaking changes

For changes that break backward compatibility, use `!` before the colon and/or a `BREAKING CHANGE: <description>` footer (allowed with any type). Do not use `!` for ordinary changes.

## Forbidden

- Creating commits or staging files without an explicit user request.
- Adding `Co-Authored-By` or any other mention of AI involvement in commits and PR descriptions.
- Uninformative messages, excessive detail, duplicating the header in the body.

## Examples

```text
fix(module): correct invalid behavior
```

```text
chore: update project configuration
```

```text
feat(module): extend existing functionality

- add new behavior (support additional scenarios)
- update validation (handle invalid input)
- fix condition handling (wrong result for empty value)

Note: update the configuration after deployment, or the new behavior will stay unavailable.
```

```text
feat(module)!: change public interface

BREAKING CHANGE: the previous interface is no longer supported.
```

## Pull request description

1. Analyze the changes relative to the target branch.
2. State the main goal briefly and group changes by meaning.
3. Mark breaking changes and required manual steps.
4. Add nothing unconfirmed; do not claim tests were run if they were not.
5. Do not mention AI involvement.

```text
## Summary

- add new functionality
- update existing behavior

## Testing

- verify expected behavior

## Notes

- required manual actions, if any
```

Add sections only when there is something to put in them.
