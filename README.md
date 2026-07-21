# Pi Memory Extension

> A persistent memory extension for Pi Coding Agent.
> Human-curated, Markdown-stored, Git-versioned long-term knowledge for Pi.
> v1 focuses on Pi only — not a replacement for Codex / Claude memory systems.

## Philosophy

1. **Human decides what becomes memory.** Only human-approved knowledge enters authoritative files.
2. **Markdown is the source of truth.** Plain text, Git-diffable, reviewable, revertible.
3. **Session history is not memory.** Pi JSONL stores raw conversations; `memory/` stores distilled knowledge.

## Installation

```bash
# From npm (recommended)
pi install npm:pi-memory-extension

# Or from GitHub
pi install git:git@github.com:appleface2050/pi-memory-extension.git

# Restart Pi or /reload
```

## Quick Start

```bash
# 1. Initialize Global Memory (personal preferences, cross-project knowledge)
/memory:init global

# 2. Initialize Workspace Memory (project-specific knowledge)
cd your-project
/memory:init workspace

# 3. Check status
/memory:status
/memory:list
```

## Commands

| Command | Description |
|---------|-------------|
| `/memory:init global` | Initialize `~/.pi/memory/` (personal layer) |
| `/memory:init workspace` | Initialize `.pi/memory/` in current project |
| `/memory:status` | Show detailed loaded memory info |
| `/memory:list` | Show file counts for Global and Workspace |
| `/memory:refresh` | Reload all memory files |
| `/memory:checkpoint` | Generate session summary to workspace inbox (requires workspace) |
| `/memory:promote <file> <targetDir> <targetFile>` | Promote inbox content to authoritative file |
| `/memory:clear-task` | Clear state/current-task.md (interrupt recovery done) |

## Storage Layout

### Global Memory (`~/.pi/memory/`)

```
~/.pi/memory/
├── user/                       # Personal preferences
│   ├── preferences.md
│   ├── coding-style.md
│   └── tools.md
├── facts/                      # Background facts
│   ├── environment.md
│   └── references.md
├── knowledge/                  # Cross-project knowledge
│   ├── decisions.md
│   ├── patterns.md
│   ├── lessons.md
│   └── bugs.md
├── state/                      # Working state
│   └── current-task.md
├── inbox/                      # Pending memory candidates
└── archive/                    # Historical archive
```

### Workspace Memory (`project/.pi/memory/`)

```
project/.pi/memory/
├── decisions.md
├── patterns.md
├── lessons.md
├── experiments.md
├── inbox/
└── archive/
```

## Design Document

See [docs/design.md](docs/design.md) for the full design specification.

## License

MIT
