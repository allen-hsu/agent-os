# Template: New Agent Setup

To create a new agent, create a directory under `agents/` with:

## Required Files

### CLAUDE.md (~80 lines)
```markdown
# [Agent Name] — [Role Title]

## Identity
- Role: [what this agent does]
- Type: Executor | Coordinator
- Reports to: Chief Orchestrator

## Behavioral Norms
- [how this agent approaches work]
- [quality standards]
- After significant tasks, run `skills/reflect.md` (or root `skills/reflect.md`)

## Available Resources (read on demand)
- `memory/MEMORY.md` — my persistent knowledge
- `memory/daily/` — daily work logs
- `memory/long-term/` — accumulated patterns and lessons
- `skills/` — my specialized SOPs
- Root `skills/` — shared team skills
```

### IDENTITY.md (~10 lines)
```markdown
# [Agent Name]
## What I Do — [one line]
## Send Me — [what tasks to delegate here]
## I Need — [required input format]
## I Return — [what output to expect]
```

### memory/MEMORY.md
Empty index file for persistent knowledge.

## Directory Structure
```
agents/{name}/
|-- CLAUDE.md
|-- IDENTITY.md
|-- memory/
|   |-- MEMORY.md
|   |-- daily/
|   +-- long-term/
+-- skills/
```
