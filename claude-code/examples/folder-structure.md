# CLAUDE.md Example: Folder Structure

Tell Claude how your notes are organized so it can find and file things correctly.

```markdown
## Folder Structure

My notes are organized as follows:

- **Team/**: Person-centric folders for each direct report
  - **[Name]/1-1s/**: 1:1 meeting notes
  - **[Name]/feedback/**: Performance notes, feedback given
- **Projects/**: One folder per project I'm tracking
  - **[Project]/**: Meeting notes, docs, status updates
- **Partners/**: External relationships
  - **[Partner]/**: Partner-specific communications
- **Meetings/**: General meeting notes not fitting elsewhere
- **_Templates/**: Reusable templates (1:1, meeting notes, etc.)
- **_Weekly Plans/**: Saved weekly planning outputs

### File Naming Convention
Use this format for new files:
```
[type]_[Topic-Name]_[YYYY-MM-DD].md
```

Types: meeting, doc, strategy, draft, template, report

Examples:
- `meeting_Alpha-Kickoff_2024-03-15.md`
- `doc_Team-Processes.md`
- `report_Weekly-Update_2024-03-18.md`

### Key Files
- `INDEX.md`: Central reference for people, projects, current state
- `log.md`: Activity log / journal
```

## Why This Helps

- **Filing**: Claude knows where to save meeting summaries
- **Finding**: Claude can locate relevant context for any topic
- **Consistency**: New files follow your conventions

## Routing Logic

Give Claude explicit routing rules:

```markdown
### Meeting Note Routing
| Meeting Type | Save Location |
|--------------|---------------|
| 1:1 with direct report | Team/[Name]/1-1s/ |
| Project meeting | Projects/[Project]/ |
| Partner call | Partners/[Partner]/ |
| General/other | Meetings/ |
```
