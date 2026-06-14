[![skills.sh](https://skills.sh/b/dayton-bobbitt/agent-skills)](https://skills.sh/dayton-bobbitt/agent-skills)

# agent-skills

A collection of custom [agent skills](https://www.skills.sh/) for use with Claude Code and other agents.

## Install

Install everything in this repo:

```sh
npx skills add dayton-bobbitt/agent-skills
```

Or install a single skill:

```sh
npx skills add dayton-bobbitt/agent-skills/retro
npx skills add dayton-bobbitt/agent-skills/pensieve
```

## Skills

| Skill | Description |
| --- | --- |
| [`retro`](skills/retro/SKILL.md) | Review conversation history, recommend improvements, and update memory. |
| [`pensieve`](skills/pensieve/SKILL.md) | Scan project-specific memories across `~/.claude/projects` and promote the globally-applicable ones to `~/AGENTS.md`. |

## Layout

Skills live under `skills/<name>/SKILL.md`, the flat layout the [skills CLI](https://www.skills.sh/docs) discovers automatically. Each `SKILL.md` has YAML frontmatter (`name`, `description`) followed by the instructions the agent loads when the skill is invoked.

```
skills/
  retro/
    SKILL.md
  pensieve/
    SKILL.md
```

To add a new skill, create a directory under `skills/` and drop a `SKILL.md` inside.
