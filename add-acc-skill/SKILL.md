---
name: add-acc-skill
description: Create a new skill in the ACC shared skills repo
user_invocable: true
---

# Add a New ACC Skill

## Instructions

1. **Gather information.** Ask the user for:
   - Skill name (must be kebab-case, e.g. `mews-debug`)
   - A short description (one sentence)
   - Whether it should be `user_invocable: true` (a slash command) or reference content (no user_invocable field)

2. **Create the skill directory and file.**
   - Create directory: `~/.claude/skills/acc-skills/<skill-name>/`
   - Create `SKILL.md` with YAML frontmatter:
     ```yaml
     ---
     name: <skill-name>
     description: <description>
     user_invocable: true  # only if user-invocable
     ---
     ```
   - Add a `# Title` heading and `## Instructions` section with a skeleton based on what the user describes.

3. **Commit the new skill.**
   - `cd ~/.claude/skills/acc-skills`
   - `git add <skill-name>/SKILL.md`
   - `git commit -m "Add <skill-name> skill"`
   - Ask the user if they want to push (`git push`).

4. **Remind the user** that teammates will get the new skill on their next `git pull` or by running `/update-acc-skills`.
