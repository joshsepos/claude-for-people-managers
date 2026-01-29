# Transcript Processing Workflow

Convert meeting recordings and transcripts into structured summaries and action items.

## The Problem

Meetings generate valuable information that quickly gets lost:
- Key decisions buried in hour-long recordings
- Action items verbally agreed but never tracked
- Context for future reference scattered or missing
- Time spent manually reviewing recordings

## The Solution

Automate the extraction of value from meeting transcripts:
1. Ingest raw transcript (from Zoom, Teams, Otter, etc.)
2. Identify meeting type and participants
3. Extract key discussion points
4. Pull out action items with owners
5. Categorize and file appropriately
6. Create tasks in your task management system

## Required Context

| Context | Purpose |
|---------|---------|
| Transcript source folder | Where raw transcripts land |
| Output folder structure | Where to file processed summaries |
| Task system access | Create action items automatically |
| Category definitions | How to route different meeting types |

## Meeting Type Routing

Different meetings need different handling:

| Meeting Type | Output Location | Special Handling |
|--------------|-----------------|------------------|
| 1:1 with direct report | Person's folder | Use 1:1 template |
| Project meeting | Project folder | Link to project context |
| Partner/external | Partner folder | Note external participants |
| General/misc | Communications folder | Basic summary |

## Inputs

- **Transcript file(s)**: Raw .txt, .vtt, or similar
- **Auto-categorize**: Let Claude determine type, or specify manually

## Outputs

- Structured markdown summary with:
  - Date, attendees, meeting type
  - Key discussion points
  - Decisions made
  - Action items (with owners)
  - Open questions
- Tasks created in task system
- Source transcript archived

## Implementation

- **Claude Code**: See `claude-code/skills/transcript-processing.md`
- **Claude Desktop**: See `claude-desktop/projects/transcript-processing.md`

## Customization Ideas

- Add sentiment analysis for team health tracking
- Extract commitments made by others for follow-up
- Generate follow-up email drafts
- Link related meetings together
- Add speaker identification for multi-party meetings
