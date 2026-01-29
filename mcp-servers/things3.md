# Things 3 MCP Integration

Connect Claude to Things 3 for reading and creating tasks.

## Platform Availability

- **macOS**: Full support via things3-mcp server
- **iOS**: Things 3 app works, but no direct Claude integration

## Claude Code Setup

### Install things3-mcp

```bash
# Via npm
npm install -g things3-mcp

# Or via Homebrew (if available)
brew install things3-mcp
```

### Get Auth Token

Things 3 uses authentication tokens for write access:

1. Open Things 3
2. Go to Settings → General → Enable Things URLs
3. Generate an auth token

### Add MCP Server

```bash
claude mcp add things3 /path/to/things3-mcp -s user -e THINGS3_AUTH_TOKEN=your_token_here
```

Find the path with: `which things3-mcp`

### Verify

```bash
claude mcp list
```

Should show `things3` as connected.

## Claude Desktop Setup

1. Open Claude Desktop settings
2. Navigate to MCP Servers section
3. Add new server:
   - Name: `things3`
   - Command: `/path/to/things3-mcp`
   - Environment: `THINGS3_AUTH_TOKEN=your_token`

## Available Operations

Once connected, Claude can:

### Read Tasks
- List todos by filter (today, upcoming, anytime, someday)
- List todos by project or area
- Search tasks by text
- Get task details by ID

### Write Tasks
- Create new todos
- Update existing todos
- Complete/uncomplete tasks
- Move tasks between projects
- Update dates (when, deadline)
- Add/remove tags

### Projects & Areas
- List projects
- Create projects
- List areas

## Usage Examples

In Claude Code:
```
"What do I have scheduled for today?"
"Create a task to follow up with Alex about the project"
"Move all my Partner tasks to Wednesday"
"What tasks mention budget?"
```

## Workflow Integration

### Weekly Planning
- Read all scheduled tasks
- Move misaligned tasks to correct days
- Create 1:1 prep tasks

### Meeting Processing
- Create action items from meeting notes
- Link tasks to source documents

### 1:1 Prep
- Search for tasks mentioning the person
- Find tasks assigned to them

## Troubleshooting

### "Things 3 not running"
Launch Things 3 before using MCP commands.

### Write operations fail
Verify your auth token is correct and hasn't expired.

### Tasks not appearing
Things 3 may take a moment to sync. Check if tasks appear in the app.

## Alternatives

If you don't use Things 3:
- **Todoist**: todoist-mcp server
- **Linear**: Linear MCP integration
- **Apple Reminders**: reminders-mcp
- **Notion**: Notion MCP

Check [MCP server directory](https://github.com/modelcontextprotocol/servers) for available integrations.
