# MCP Servers for Manager Workflows

Model Context Protocol (MCP) servers extend Claude's capabilities by connecting to external tools and services.

## What is MCP?

MCP is a standard protocol for connecting AI assistants to tools. Instead of Claude just reading and writing text, MCP lets Claude:
- Read from your task manager
- Query your calendar
- Access databases
- Interact with APIs

## Relevant Servers for Managers

| Server | Purpose | Platform |
|--------|---------|----------|
| [things3](things3.md) | Task management (macOS) | Claude Code, Desktop |
| [calendar](calendar.md) | Meeting awareness | Claude Code, Desktop |
| todoist | Task management (cross-platform) | Claude Code, Desktop |
| linear | Issue tracking | Claude Code, Desktop |
| notion | Notes and databases | Claude Code, Desktop |
| atlassian | Jira/Confluence | Claude Code, Desktop |

## Setup Patterns

### Claude Code (CLI)

```bash
# Stdio servers (local binaries)
claude mcp add <name> /path/to/server -s user

# HTTP servers (remote services)
claude mcp add --transport http <name> <url> -s user

# With environment variables
claude mcp add <name> /path/to/server -s user -e KEY=value
```

Scope options:
- `user`: Available in all projects (~/.claude.json)
- `local`: This project only (.claude.json)
- `project`: Shared with team (.mcp.json)

### Claude Desktop

1. Open Settings
2. Go to MCP Servers
3. Add server with name, command, and environment

## Choosing Servers

### Task Management
Pick based on what you use:
- Things 3 → things3-mcp
- Todoist → todoist-mcp
- Linear → linear-mcp
- Apple Reminders → reminders-mcp

### Calendar
Pick based on your calendar system:
- Microsoft 365 → microsoft365 MCP
- Google Workspace → gcal-mcp (community)
- Apple Calendar → AppleScript (no MCP needed)

### Notes/Knowledge
- Obsidian → obsidian-mcp
- Notion → notion-mcp
- Confluence → atlassian MCP

## Security Considerations

MCP servers can:
- Read your data
- Create/modify content (if authenticated)
- Access credentials you provide

**Best practices:**
- Only install servers from trusted sources
- Review what permissions each server needs
- Use read-only access when write isn't needed
- Rotate tokens periodically

## Troubleshooting

### Server not connecting
```bash
claude mcp list  # Check status
```

### HTTP server auth errors
Re-authenticate: `/mcp` in Claude Code

### Server crashes
Check logs, ensure dependencies are installed.

## Resources

- [MCP Protocol Spec](https://github.com/modelcontextprotocol/protocol)
- [MCP Server Directory](https://github.com/modelcontextprotocol/servers)
- [Building MCP Servers](https://modelcontextprotocol.io/docs/servers)
