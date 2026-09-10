# Agent Skills

A collection of shared [agent skills](https://agentskills.io) used across my different machines.

Each skill lives in its own directory with a `SKILL.md` file describing when and how to use it.

## Skills

| Skill | Description |
|---|---|
| [skill-management](skill-management/) | Create new agent skills or update existing ones following the [Agent Skills specification](https://agentskills.io/specification.md). |

## Usage

This repo is a [pi package](https://pi.dev/packages). Install it with:

```sh
pi install git:github.com/mydnicq/agent-skills
```

Keep the skills up to date with:

```sh
pi update --extensions
```