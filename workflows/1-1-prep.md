# 1:1 Prep Workflow

Prepare for 1:1 meetings with direct reports by gathering relevant context automatically.

## The Problem

Before a 1:1, you need to remember:
- What you discussed last time
- What action items were assigned (yours and theirs)
- What's been happening on their projects
- What you've been meaning to bring up

This takes 10-15 minutes of digging through notes, tasks, and memory. Or you wing it and miss things.

## The Solution

Let Claude gather and synthesize this context in seconds:
1. Pull recent 1:1 notes for this person
2. Find open action items (yours and theirs)
3. Check for "parked" topics from previous meetings
4. Surface relevant project updates
5. Present a structured prep document

## Required Context

For this workflow to function, Claude needs access to:

| Context | Purpose |
|---------|---------|
| 1:1 history | Past meeting notes to review |
| Task system | Open action items and commitments |
| Team roster | Who reports to you |
| Parked topics | Things deferred from previous 1:1s |

## Inputs

- **Name**: Which direct report you're meeting with
- **Depth** (optional): Quick summary vs. detailed prep

## Outputs

- Summary of last 1:1 (key points, not full transcript)
- Open action items for both parties
- Parked topics to potentially revisit
- Suggested discussion points based on recent context
- Any time-sensitive items (upcoming deadlines, reviews, etc.)

## Implementation

- **Claude Code**: See `claude-code/skills/1-1-prep.md`
- **Claude Desktop**: See `claude-desktop/projects/1-1-prep.md`

## Customization Ideas

- Add integration with your calendar to show upcoming events for this person
- Pull from performance review cycle dates
- Include project status from Jira/Linear
- Add team health survey data if available
