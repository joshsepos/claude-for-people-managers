# Calendar MCP Integration

Connect Claude to your calendar for meeting awareness.

## Options

Several approaches to calendar integration:

### 1. Microsoft 365 MCP (Recommended for M365 users)

Official Anthropic integration for Outlook/M365 calendars.

**Setup (Claude Code):**
```bash
claude mcp add --transport http microsoft365 https://microsoft365.mcp.claude.com/mcp -s user
```

**Authentication:**
- First use will prompt OAuth login
- Re-authenticate with `/mcp` if token expires

**Capabilities:**
- Read calendar events
- See meeting details (attendees, location)
- Time-based queries ("what's on my calendar tomorrow")

### 2. Google Calendar MCP

For Google Workspace users.

Check [MCP server directory](https://github.com/modelcontextprotocol/servers) for community implementations.

### 3. Apple Calendar via AppleScript (macOS)

No MCP needed - use shell commands.

**Example (in Claude Code skills):**
```bash
osascript -e '
tell application "Calendar"
    set output to ""
    repeat with c in calendars
        set evts to (every event of c whose start date >= (current date))
        repeat with e in evts
            set output to output & (summary of e) & " - " & (start date of e) & linefeed
        end repeat
    end repeat
    return output
end tell'
```

**Permissions required:**
- System Settings → Privacy → Automation → Allow Terminal to control Calendar

### 4. Manual / Paste

For Claude Desktop or when MCP isn't available:
- Copy your week's calendar
- Paste into conversation
- Claude can work with text representation

## Useful Calendar Queries

Once integrated:

```
"What's on my calendar this week?"
"Do I have any meetings tomorrow afternoon?"
"When is my next 1:1 with Alex?"
"Show me all meetings with Partner Corp"
"What days are heavy with meetings?"
```

## Workflow Integration

### Weekly Planning
- Calculate meeting hours per day
- Identify focus time vs meeting time
- Flag days with >5 hours of meetings

### Meeting Prep
- Confirm meeting is actually scheduled
- Note attendees and any pre-set agenda
- Check for back-to-back constraints

### 1:1 Prep
- Verify 1:1 is on the calendar
- Note if it was rescheduled recently

## Privacy Considerations

Calendar MCP servers have access to:
- Meeting titles and descriptions
- Attendee names and emails
- Times and locations

Review the MCP server's privacy policy before connecting.

## Limitations

Most calendar MCPs are **read-only**:
- Cannot create events
- Cannot accept/decline invitations
- Cannot modify existing events

This is generally appropriate - calendar writes are high-stakes actions.
