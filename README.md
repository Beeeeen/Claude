# claude-config

Personal Claude Code configuration — settings, global preferences, and per-project memory.

## Structure

```
~/.claude/
├── settings.json              # Global Claude Code settings
├── projects/
│   ├── <project-hash>/
│   │   └── memory/            # Per-project persistent memory
│   │       ├── MEMORY.md      # Memory index (auto-loaded each session)
│   │       ├── user_profile.md
│   │       ├── feedback_*.md
│   │       ├── project_*.md
│   │       └── reference_*.md
└── README.md
```

## Memory Types

| Type | Purpose | Example |
|------|---------|---------|
| `user_*.md` | Your background, role, expertise | Language preferences, skill level |
| `feedback_*.md` | How Claude should behave | Response style, things to avoid |
| `project_*.md` | Project context and decisions | Architecture choices, current status |
| `reference_*.md` | Where to find external info | Linear boards, dashboards, docs |

## New Machine Setup

```bash
# 1. Clone repo
git clone git@github.com:<you>/claude-config.git ~/.claude

# 2. Done — Claude Code reads memory automatically on next session
```

## Daily Workflow

Claude writes memory automatically during conversations. You don't need to do anything manually.

To **manually save** something:
> "記住：..."

To **forget** something:
> "忘掉關於 X 的記憶"

## Updating This Repo

```bash
cd ~/.claude

# Check what changed
git status
git diff

# Commit (after Claude updates memory during a session)
git add projects/ settings.json
git commit -m "update memory: <what changed>"
git push
```

## When to Commit

- After a session where important context was established
- After changing `settings.json`
- Before switching machines

## Adding a New Project

Claude auto-creates the `projects/<hash>/memory/` folder when you start a new project.
The hash is derived from the project's absolute path.

To find a project's hash:
```bash
ls ~/.claude/projects/
```

## Syncing to New Machine

```bash
# On new machine
git clone git@github.com:<you>/claude-config.git ~/.claude

# Verify memory loaded
# Start Claude Code in any project — it will read from projects/<hash>/memory/
```
