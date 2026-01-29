# Status Rollup Workflow

Generate quick status summaries for projects, partners, or initiatives.

## The Problem

You need to give updates on things you're tracking:
- "What's the status on Project X?"
- "How are things going with Partner Y?"
- "What's happening with Initiative Z?"

The information exists across meeting notes, documents, and tasks - but synthesizing it on demand takes time.

## The Solution

Let Claude aggregate status from your existing notes:
1. Identify the subject (project, partner, person, initiative)
2. Gather recent activity (meeting notes, documents, tasks)
3. Synthesize into a coherent status summary
4. Highlight blockers and next steps

## Required Context

| Context | Purpose |
|---------|---------|
| Organized notes folder | Meeting notes and documents by subject |
| Task system (optional) | Open tasks related to subject |
| Time range | How far back to look |

## Depth Levels

| Level | Use Case | Output |
|-------|----------|--------|
| Quick | Slack response, hallway question | 2-3 sentences |
| Standard | Status meeting, email update | Paragraph with bullets |
| Detailed | Executive review, planning session | Full page with history |

## Inputs

- **Subject**: Project name, partner name, or initiative
- **Depth**: Quick / Standard / Detailed
- **Time range** (optional): Last week, last month, all time

## Outputs

- Status summary at requested depth
- Key recent activities
- Current blockers or risks
- Next steps / upcoming milestones
- Open questions or decisions needed

## Implementation

- **Claude Code**: See `claude-code/skills/status-rollup.md`
- **Claude Desktop**: See `claude-desktop/projects/status-rollup.md`

## Customization Ideas

- Add Jira/Linear integration for ticket status
- Include GitHub activity for technical projects
- Generate different formats (Slack, email, slide)
- Track status over time for trends
