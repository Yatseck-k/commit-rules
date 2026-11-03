# commit-rules

**An AI coding agent skill for Conventional Commits and pull request descriptions.**

[Русский](README.ru.md) · [Skill instructions](SKILL.md) · [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/)

![Git](https://img.shields.io/badge/Focus-Git-F05032?logo=git&logoColor=white) ![AI agents](https://img.shields.io/badge/AI-agent%20skill-374151)

## Overview

`commit-rules` turns a repository's actual changes into concise, consistent **English commit messages** and **PR descriptions**. It works with coding agents that support `SKILL.md`, without application dependencies.

The agent examines the branch, working tree, staged and unstaged diffs, and recent commits. It **does not stage or commit changes** unless explicitly requested.

## Features

| Feature | Behavior |
| --- | --- |
| **Conventional Commits** | Selects a suitable `type` and optional `scope` from the diff |
| **Accurate summaries** | Prioritizes staged changes when present; branch name is only a hint |
| **Short bodies** | Describes meaningful changes in compact action-oriented bullets |
| **Breaking changes** | Supports `!` and `BREAKING CHANGE:` |
| **Deployment notes** | Includes `Note:` when manual actions are necessary |
| **Pull requests** | Drafts Summary, Testing, and Notes sections |
| **Explicit actions** | No automatic staging, committing or AI co-author lines |

## Installation

Copy [SKILL.md](SKILL.md) into the directory for your coding agent's skills:

```text
<agent-skills-directory>/commit-rules/SKILL.md
```

If the agent does not support skills, adapt its instructions in the project's agent configuration file.

## Usage

Ask your agent to:

```text
Write a commit message for the current changes.
Write a pull request description for this branch.
```

Example output:

```text
feat(api): add task filtering

- add status filters to task search
- validate filter inputs to reject unsupported values
- cover filtering behavior with tests
```

The agent derives the actual content from the repository. It should not fabricate implementation details or test results. See [SKILL.md](SKILL.md) for precise rules and restrictions.

## Repository structure

```text
SKILL.md      Complete agent instructions
README.md     English overview
README.ru.md  Russian overview
```

## Related projects

- [ub-mode-php](https://github.com/Yatseck-k/ub-mode-php) — independent disciplined PHP coding skill.
- [ub-cdmu-php](https://github.com/Yatseck-k/ub-cdmu-php) — optional PHP quality analysis CLI.

`commit-rules` works independently of both projects.
