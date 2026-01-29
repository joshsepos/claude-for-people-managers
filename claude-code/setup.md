# Claude Code Setup for Managers

How to configure Claude Code for manager workflows.

## Prerequisites

- Claude Code CLI installed (`npm install -g @anthropic-ai/claude-code` or via Homebrew)
- A notes folder structure (Obsidian, plain markdown, etc.)
- Optional: Task management app with MCP support

## Step 1: Install Skills

Copy the skills from this repo to your user skills folder:

```bash
# Create skills directory if it doesn't exist
mkdir -p ~/.claude/skills

# Copy each skill
cp -r claude-code/skills/1-1-prep ~/.claude/skills/
cp -r claude-code/skills/weekly-planning ~/.claude/skills/
cp -r claude-code/skills/status-rollup ~/.claude/skills/
cp -r claude-code/skills/meeting-prep ~/.claude/skills/
```

Each skill is a folder with a `SKILL.md` file inside.

## Step 2: Configure Your CLAUDE.md

Create or update your project's `CLAUDE.md` with context about your team and workflows.

Use the examples in `examples/` as starting points:
- `team-context.md` - Your direct reports and 1:1 schedule
- `aor-schedule.md` - Your focus areas by day
- `folder-structure.md` - How your notes are organized

Minimum viable CLAUDE.md for manager workflows:

```markdown
# Manager Context

## Direct Reports
- Alex Chen
- Jordan Smith
- Sam Wilson

## 1:1 Schedule
Tuesday: Alex, Jordan
Thursday: Sam

## Notes Location
- 1:1 notes: ~/Documents/Notes/Team/[Name]/1-1s/
- Projects: ~/Documents/Notes/Projects/

## Task Management
Using Things 3 via MCP server.
```

## Step 3: Configure MCP Servers (Optional)

MCP servers extend Claude's capabilities. For manager workflows, useful servers include:

### Things 3 (macOS)
```bash
claude mcp add things3 /path/to/things3-mcp -s user
```

### Calendar Integration
See `mcp-servers/calendar.md` for options.

### Verify Configuration
```bash
claude mcp list
```

## Step 4: Customize Skills

Each skill has a Configuration section at the top. Update:
- Your direct reports list
- File paths to match your structure
- Task system and project names

## Usage

Once configured, invoke skills naturally:

```
/1-1-prep Alex
/weekly-planning
/status-rollup Project Alpha
/meeting-prep Pat Director
```

Or let Claude detect context and suggest relevant workflows.

## Troubleshooting

### Skills not appearing
- Check `~/.claude/skills/` contains folders with `SKILL.md` files
- Restart Claude Code after adding skills

### MCP server errors
- Run `claude mcp list` to check connection status
- For HTTP servers, re-authenticate with `/mcp` if token expired

### Claude can't find files
- Verify paths in CLAUDE.md match your actual folder structure
- Use absolute paths or `~` for home directory
