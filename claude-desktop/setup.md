# Claude Desktop Setup for Managers

How to configure Claude Desktop for manager workflows.

## Overview

Claude Desktop uses **Projects** instead of skills. Each Project has:
- **Custom instructions**: Persistent context Claude remembers
- **Files**: Documents Claude can reference
- **Conversations**: Chat history within the project

## Approach

Create a "Manager Hub" project with your context, then use prompts from the `prompts/` folder to trigger specific workflows.

## Step 1: Create Manager Project

1. Open Claude Desktop
2. Click "Projects" in the sidebar
3. Click "New Project"
4. Name it "Manager Hub" (or similar)

## Step 2: Add Custom Instructions

Click "Edit project instructions" and paste content from `projects/manager-hub.md`.

This gives Claude persistent context about:
- Your team structure
- Your focus areas
- Your file organization
- Your preferences

## Step 3: Add Reference Files (Optional)

If you have key reference documents, add them to the project:
- Team roster / org chart
- Project status summaries
- Templates you use frequently

Claude can reference these in conversations.

## Step 4: Use Workflow Prompts

The `prompts/` folder contains ready-to-use prompts for each workflow:
- `1-1-prep.txt` - Copy/paste when prepping for a 1:1
- `weekly-planning.txt` - Copy/paste for weekly review
- `status-rollup.txt` - Copy/paste for status updates
- `meeting-prep.txt` - Copy/paste before stakeholder meetings

You can also save these as "Starred" messages for quick access.

## Workflow

Typical usage:

1. Open your Manager Hub project
2. Start a new conversation
3. Paste the relevant prompt
4. Provide any additional context (paste meeting notes, etc.)
5. Claude generates the output

## Limitations vs Claude Code

| Feature | Claude Code | Claude Desktop |
|---------|-------------|----------------|
| File system access | Full | Must paste content or add to project |
| Task management | MCP servers (Things 3, etc.) | Manual or paste task lists |
| Automation | Skills auto-trigger | Manual prompt invocation |
| Calendar | MCP integration | Paste or describe schedule |

## Tips for Desktop Users

### Paste Liberally
Since Desktop can't read files directly, paste relevant content:
- Last 1:1 notes before prep
- Task list before weekly planning
- Recent meeting notes before status rollup

### Use Artifacts
Claude Desktop can create Artifacts - use them for:
- Formatted prep documents you can copy elsewhere
- Tables and structured output
- Templates to reuse

### Keep Conversations Focused
Start a new conversation for each discrete task. This keeps context clean and makes conversations easier to find later.
