# Manager Workflows for Claude

Reusable AI workflows for engineering managers and people leaders, designed for both **Claude Code** (CLI) and **Claude Desktop** (GUI).

## The Gap

Claude's ecosystem is heavily developer-focused: test runners, linters, code review, debugging. But managers have workflows too:

- Preparing for 1:1s with direct reports
- Processing meeting transcripts into actionable summaries
- Weekly planning and task alignment
- Status rollups for stakeholders
- Performance review preparation

This repo provides ready-to-use implementations of these workflows for both Claude platforms.

## Structure

```
manager-workflows/
├── workflows/           # Platform-agnostic: what each workflow does and why
├── claude-code/         # Skills and CLAUDE.md examples for CLI users
├── claude-desktop/      # Project templates and prompts for Desktop users
└── mcp-servers/         # Tool integrations (Things 3, calendar, etc.)
```

## Quick Start

### Claude Code Users

1. Copy skills from `claude-code/skills/` to `~/.claude/skills/`
2. Add relevant snippets from `claude-code/examples/` to your `CLAUDE.md`
3. Configure MCP servers per `mcp-servers/` guides
4. Invoke skills with `/skill-name` or let Claude detect context

### Claude Desktop Users

1. Create a new Project in Claude Desktop
2. Copy instructions from `claude-desktop/projects/` into Project instructions
3. Configure MCP servers in Desktop settings
4. Use prompts from `claude-desktop/prompts/` as conversation starters

## Workflows

| Workflow | Purpose |
|----------|---------|
| [1:1 Prep](workflows/1-1-prep.md) | Gather context before meeting with direct reports |
| [Weekly Planning](workflows/weekly-planning.md) | Align tasks with focus areas for the week |
| [Transcript Processing](workflows/transcript-processing.md) | Convert meeting recordings into summaries and action items |
| [Status Rollup](workflows/status-rollup.md) | Generate status updates for projects or partners |
| [Meeting Prep](workflows/meeting-prep.md) | Prepare for stakeholder meetings |

## Philosophy

### Context is King

The power of these workflows comes from giving Claude access to your working context:
- Past meeting notes and 1:1 history
- Team structure and relationships
- Project status and priorities
- Your task management system

Without context, Claude gives generic advice. With context, it becomes a thought partner.

### Progressive Disclosure

Start simple. A basic `CLAUDE.md` with your team list and 1:1 schedule provides value immediately. Add complexity (MCP integrations, detailed workflows) as you see the benefit.

### Adapt, Don't Adopt

These workflows reflect one manager's preferences. Your team, your tools, your style are different. Use these as starting points, not prescriptions.

## Requirements

- **Claude Code**: v1.0+ with Skills support
- **Claude Desktop**: Any recent version with Projects
- **Optional**: Things 3 (macOS/iOS), Obsidian, calendar integration

## Contributing

Found a workflow that helps you manage? PRs welcome. The goal is practical patterns that work, not theoretical frameworks.

## License

MIT - Use freely, adapt liberally, share generously.
