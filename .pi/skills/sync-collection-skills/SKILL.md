---
name: sync-collection-skills
description: Sync skills vendored in this collection with their upstream sources. Use when asked to update, refresh, re-sync, or check a collection skill against upstream, or when adding a new upstream-tracked skill to the registry.
---

# Sync Collection Skills

Skills in this collection are verbatim copies of upstream files. Never hand-edit a vendored `SKILL.md`.

## Rules

1. **Copy verbatim.** No rewording, no frontmatter edits, no formatting fixes.
2. **Track the newest stable release tag**, never the default branch. Upstream marks previews as prereleases, so they are skipped automatically.
3. **Verify before committing.** The fetched file and the vendored file must be byte-identical, and `git diff` must show only intended upstream changes.
4. **A sync touches one file.** Update `README.md` and `package.json` only when adding a skill, never when re-syncing one.
5. **Report** the source ref and SHA-256. If upstream is unchanged, say so and stop.

## Registry

| Skill | Upstream | Path | Ref |
|---|---|---|---|
| herdr | herdrdev/herdr | skills/herdr/SKILL.md | newest stable `v*` release |
| write-discoverable-code | modem-dev/skills | write-discoverable-code/SKILL.md | `main` (no release tags) |

Locally-owned skills (not tracked upstream, never auto-synced): `skill-management`.

## Update herdr

```sh
tag=$(curl -s https://api.github.com/repos/herdrdev/herdr/releases/latest | grep -o '"tag_name": "[^"]*"' | cut -d'"' -f4)
curl -sL "https://raw.githubusercontent.com/herdrdev/herdr/$tag/skills/herdr/SKILL.md" -o herdr/SKILL.md
shasum -a 256 herdr/SKILL.md
git diff --stat herdr/SKILL.md
```

Commit as `chore(herdr): sync skill to <tag>` once the diff contains only upstream changes.

## Update write-discoverable-code

```sh
curl -sL https://raw.githubusercontent.com/modem-dev/skills/main/write-discoverable-code/SKILL.md -o write-discoverable-code/SKILL.md
shasum -a 256 write-discoverable-code/SKILL.md
git diff --stat write-discoverable-code/SKILL.md
```

Upstream has no release tags, so track `main` and commit as `chore(write-discoverable-code): sync skill to <sha>` once the diff contains only upstream changes.

To track a new skill: add a registry row, copy the upstream file verbatim to `<skill>/SKILL.md`, and register it in `package.json` under `pi.skills` and in the `README.md` table.
