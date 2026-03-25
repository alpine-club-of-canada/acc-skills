# ACC Shared Skills for Claude Code

Shared Claude Code skills for the Alpine Club of Canada (ACC) technology team.

These skills provide team-wide conventions, debugging guides, and scaffolding tools for working with ACC's technology stack (HubSpot, Mews, QuickBooks Online, etc.).

## Install

Paste this into Claude Code:

> Install acc-skills: run `git clone https://github.com/alpine-club-of-canada/acc-skills.git ~/.claude/skills/acc-skills`

Or run it directly in your terminal:

```bash
git clone https://github.com/alpine-club-of-canada/acc-skills.git ~/.claude/skills/acc-skills
```

Once installed, Claude Code will automatically pick up the skills in this repo.

## Update

Pull the latest skills:

```bash
cd ~/.claude/skills/acc-skills && git pull
```

Or use the `/update-acc-skills` skill from within Claude Code.

## Available Skills

| Skill | Description | Invocable |
|-------|-------------|-----------|
| `update-acc-skills` | Pull latest skills from the repo | `/update-acc-skills` |
| `hubspot-debug` | Debug HubSpot workflow and membership sync issues | Reference |
| `hubspot-coded-action` | Scaffold or review HubSpot coded actions | Reference |
| `acc-conventions` | ACC technology stack conventions | Reference |
| `add-acc-skill` | Create a new skill in this repo | `/add-acc-skill` |

## Adding New Skills

Use `/add-acc-skill` from Claude Code, or manually create a `<skill-name>/SKILL.md` with proper YAML frontmatter and open a PR.
