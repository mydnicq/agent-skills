# Agent Skills

A collection of shared [agent skills](https://agentskills.io) used across my different machines.

Each skill lives in its own directory with a `SKILL.md` file describing when and how to use it.

## Skills

| Skill | Description | Source |
|---|---|---|
| [herdr](herdr/) | Control Herdr, a terminal multiplexer for coding agents. | [herdrdev/herdr](https://github.com/herdrdev/herdr/blob/master/skills/herdr/SKILL.md) |
| [skill-management](skill-management/) | Create new agent skills or update existing ones following the [Agent Skills specification](https://agentskills.io/specification.md). | Original |
| [write-discoverable-code](write-discoverable-code/) | Rules for writing code that coding agents (and humans) can find and understand through plain-text search. | [modem-dev/skills](https://github.com/modem-dev/skills/blob/main/write-discoverable-code/SKILL.md) |

## Usage

This repo is a [pi package](https://pi.dev/packages). Install it with:

```sh
pi install git:github.com/mydnicq/agent-skills
```

Keep the skills up to date with:

```sh
pi update --extensions
```