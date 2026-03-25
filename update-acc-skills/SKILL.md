---
name: update-acc-skills
description: Pull the latest ACC shared skills from the repository
user_invocable: true
---

# Update ACC Skills

Pull the latest shared skills from the ACC skills repository.

## Instructions

1. Run `cd ~/.claude/skills/acc-skills && git pull` to fetch the latest changes.
2. Run `git log --oneline -5` to show the user what changed recently.
3. Report a summary of any new or updated skills based on the log output.
4. If the pull fails (e.g. local changes), suggest `git stash && git pull && git stash pop` or `git reset --hard origin/main` if the user is okay discarding local changes.
