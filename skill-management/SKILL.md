---
name: skill-management
description: Create new agent skills or update existing ones following the Agent Skills specification. Use when the user asks to create a skill, update a skill, modify skill files, or work with SKILL.md files. Always fetches the latest specification from https://agentskills.io/specification.md before creating or updating.
license: MIT
compatibility: Designed for pi coding agent (or similar products)
metadata:
  author: pi-agent
  version: "1.1"
---

# Skill Management

This skill handles the creation and updating of Agent Skills following the official specification from https://agentskills.io/specification.md.

## Prerequisites

Before creating or updating any skill, you MUST:

1. Fetch the latest specification from https://agentskills.io/specification.md
2. If the URL is unreachable or returns an error, STOP the process immediately
3. Validate all skill content against the fetched specification

## Location Selection

When the user wants to create or update a skill, ask them to choose the target location:

**Option 1: Global skills directory (default)**
- Path: `~/.pi/agent/skills/`
- Use for: Skills that should be available across all projects

**Option 2: Project-local skills directory**
- Path: `.agents/skills/` (relative to current working directory)
- Use for: Skills specific to the current project

If the user doesn't specify, default to Option 1 (global).

## Creating a New Skill

1. Ask the user for:
   - Skill name (must follow naming rules: lowercase, alphanumeric, hyphens only, no leading/trailing hyphens)
   - Skill description
   - Target location (Option 1 or 2)

2. Validate the skill name against the specification:
   - 1-64 characters
   - Only lowercase letters, numbers, and hyphens
   - No leading or trailing hyphens
   - No consecutive hyphens

3. Create the skill directory structure:
   ```
   skill-name/
   └── SKILL.md
   ```

4. Generate SKILL.md with proper frontmatter:
   ```yaml
   ---
   name: skill-name
   description: Description of what this skill does
   ---
   ```

5. Add skill instructions in the body section

## Updating an Existing Skill

1. Ask the user for:
   - Skill name to update
   - Target location (Option 1 or 2)
   - What specifically to update (frontmatter, body, or both)

2. Locate the skill directory and SKILL.md file

3. Read the current SKILL.md content

4. Apply the requested changes while maintaining valid frontmatter

5. Validate the updated content against the specification

## Validation Rules

Always validate skills against the specification:

- **name field**: Required, 1-64 chars, lowercase alphanumeric and hyphens only, no leading/trailing/consecutive hyphens
- **description field**: Required, 1-1024 chars, non-empty
- **license field**: Optional, string
- **compatibility field**: Optional, 1-500 chars
- **metadata field**: Optional, key-value mapping
- **allowed-tools field**: Optional, space-delimited list

## Error Handling

- If the specification URL is unreachable: STOP and inform the user
- If skill name is invalid: Ask the user to provide a valid name
- If target directory doesn't exist: Create it
- If SKILL.md already exists when creating: Ask if user wants to update instead

## Examples

### Creating a new skill

User: "Create a skill for processing JSON files"

1. Fetch specification from https://agentskills.io/specification.md
2. Ask user for location (default: ~/.pi/agent/skills/)
3. Ask user for skill name (suggest: json-processing)
4. Create directory: ~/.pi/agent/skills/json-processing/
5. Create SKILL.md with frontmatter and instructions

### Updating an existing skill

User: "Update my json-processing skill to add CSV support"

1. Fetch specification from https://agentskills.io/specification.md
2. Ask user for location
3. Read existing ~/.pi/agent/skills/json-processing/SKILL.md
4. Update description and body content
5. Validate and save
