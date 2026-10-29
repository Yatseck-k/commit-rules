# commit_rules
An agent skill that writes commit messages and PR descriptions following [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/).

It works with any AI coding agent that supports `SKILL.md` instruction files. The agent reads the repository state itself (branch, status, diff, recent log), so you don't have to describe the changes. It shows a ready message and stops.

## Features

- Builds the message from `git diff HEAD`, preferring staged changes when there are any
- Picks `type` and `scope` from the actual changes, using the branch name only as a hint
- Short list-style body: `- <action> <change> (<reason>)`
- Supports `Note:` for manual post-deploy steps and `!` / `BREAKING CHANGE:` for breaking changes
- Generates PR descriptions (Summary / Testing / Notes)
- Never commits or stages files without an explicit request
- Never adds `Co-Authored-By` or other mentions of AI

## Installation

Copy `SKILL.md` into the skills directory of your agent, in a folder named `commit-rules`:

```text
<skills-dir>/commit-rules/SKILL.md
```

Use a global skills directory to make it available in all projects, or a project-level one to share it through the repository. The exact path depends on the agent, so check its documentation.

If your agent has no skills support, add the contents of `SKILL.md` to its instruction file (for example `AGENTS.md`).

## Usage

Ask the agent in natural language:

```text
write a commit message
write a PR description
```

Example output:

```text
feat(module): extend existing functionality

- add new behavior (support additional scenarios)
- update validation (handle invalid input)

Note: update the configuration after deployment, or the new behavior will stay unavailable.
```

## Customization

Edit `SKILL.md` to fit your project:

- **Language:** messages are written in English by default.
- **Types:** the table in the `Types` section lists the allowed commit types.
- **Forbidden:** the `Forbidden` section holds hard rules, for example the ban on AI attribution lines.
