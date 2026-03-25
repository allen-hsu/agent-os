# AgentOS

A multi-agent operating system built on [Claude Code](https://docs.anthropic.com/en/docs/claude-code). A central coordinator (Chief) routes tasks to specialist agents, each with its own identity, memory, and skills.

> **[中文版說明](README.zh-TW.md)**

## Architecture

```
AgentOS
├── CLAUDE.md          # Chief — the central coordinator
├── skills/            # Shared skills available to all agents
├── templates/         # Templates for new agents & skills
├── memory/            # Cross-team shared knowledge & daily logs
└── agents/
    ├── dev/           # Code, architecture, debugging
    ├── writer/        # Writing, docs, content
    └── researcher/    # Research, analysis, fact-checking
```

## How It Works

**Chief** acts as a COO — every request lands on its desk first. It either handles the task directly or delegates to the right specialist:

| Agent | Handles |
|---|---|
| **@dev** | Feature requests, bug fixes, code reviews, architecture |
| **@writer** | Documentation, blog posts, emails, content editing |
| **@researcher** | Research questions, competitive analysis, fact-checking |

Each agent runs in an independent context window with its own `CLAUDE.md`, memory, and skills. Chief synthesizes results and reports back.

## Key Features

- **Smart Routing** — Chief reads the request and delegates to the best-fit agent
- **Persistent Memory** — Each agent maintains its own memory for patterns, lessons, and context
- **Auto Reflection** — Every agent writes a daily log after completing significant tasks (mandatory behavior, not optional)
## Getting Started

1. Install [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
2. Clone this repo
3. Run `claude` in the project root — Chief loads automatically

```bash
git clone git@github.com:allen-hsu/agent-os.git
cd agent-os
claude
```

## Scheduled Tasks

You can use standard cron or Claude Code's built-in scheduling to run recurring tasks (e.g., a daily Morning Briefing).

### Option 1: Local cron + Claude CLI

Add to your crontab (`crontab -e`):

```bash
# Morning Briefing — every day at 9am
0 9 * * * cd /Users/you/agent-os && claude -p "Execute Morning Briefing: read memory/daily/ for recent team logs, read memory/MEMORY.md for priorities, check each agent's memory/daily/ for activity, and output a concise daily briefing." >> /tmp/morning-briefing.log 2>&1
```

**Requirements**: Machine must be on, Claude CLI installed.

### Option 2: In-session cron (testing only)

Inside a Claude Code session, ask Chief to create a temporary scheduled task:

```
Run Morning Briefing every 10 minutes
```

This uses Claude Code's built-in `CronCreate` — session-only, auto-expires after 7 days.

### Available Scheduled Tasks

| Task | Skill File | Suggested Schedule |
|---|---|---|
| Morning Briefing | `skills/morning-briefing.md` | Daily at 9am |

## Adding New Agents

Use the template at `templates/new-agent.md` to scaffold a new specialist agent. Each agent needs:

- `CLAUDE.md` — Identity, principles, tools, memory, skills
- `IDENTITY.md` — Brief summary for Chief's routing decisions
- `memory/MEMORY.md` — Persistent knowledge index

## License

MIT
