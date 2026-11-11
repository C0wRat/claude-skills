# claude-skills

Personal [Claude Code](https://claude.com/claude-code) skills.

## Skills

| Skill | Purpose |
| --- | --- |
| [conventional-git](skills/conventional-git/SKILL.md) | Enforces Conventional Commits for messages and `type/slug` names for branches, with no Claude/AI attribution. |

## Install

Copy a skill folder into your skills directory:

```bash
# user-wide
cp -r skills/conventional-git ~/.claude/skills/

# or only for one project
cp -r skills/conventional-git <project>/.claude/skills/
```

Claude Code loads it automatically the next time a session starts.
