# Agent Skills

A collection of shared [agent skills](https://agentskills.io) used across my different machines.

Each skill lives in its own directory with a `SKILL.md` file describing when and how to use it.

## Skills

| Skill | Description |
|---|---|
| [skill-management](skill-management/) | Create new agent skills or update existing ones following the [Agent Skills specification](https://agentskills.io/specification.md). |

## Usage

Clone this repo and symlink (or copy) the skills you need into your agent's skill directory, e.g.:

```sh
ln -s ~/Work/Study/agent-skills/<skill-name> ~/.pi/agent/skills/<skill-name>
```

## Structure

```
agent-skills/
└── <skill-name>/
    └── SKILL.md
```