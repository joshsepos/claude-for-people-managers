# Pending Transcripts Skill - Documentation

## What This Does

Processes new Zoom meeting transcripts into organized summaries with automatic action item extraction to Things 3. This is the **daily workflow** - different from the legacy transcript processor (which handles bulk historical imports).

## How It Differs from transcript-processor

| Aspect | pending-transcripts | transcript-processor |
|--------|--------------------|--------------------|
| **Use case** | Daily/ongoing processing | Bulk historical import |
| **Source** | _Pending Transcripts/ or Zoom folder | Any folder of old transcripts |
| **Output** | One summary per meeting | Consolidated topic documents |
| **Things 3** | Auto-adds action items | Optional |
| **Cleanup** | Deletes source after processing | Preserves originals |

---

## The Pipeline

```
Zoom Recording
     ↓
~/Documents/Zoom/ (auto-save)
     ↓
Folder watcher queues to _Pending Transcripts/
     ↓
"Process my transcripts" trigger
     ↓
Claude: Read → Categorize → Summarize → Extract actions
     ↓
Summary saved to appropriate folder
Action items → Things 3
Source transcript deleted
```

---

## Categorization Rules

### Automatic Detection

The skill identifies meeting types by:

1. **Meeting title** - "1:1", "SADP", "Concepts" in filename
2. **Attendee names** - Direct reports trigger 1:1 template
3. **Keywords** - Partner names, technical terms
4. **Speaker patterns** - Who's talking about what

### Category Mapping

| Detected Pattern | Category | Output Location |
|-----------------|----------|-----------------|
| 1:1 with direct report | CE Manager | `CE Manager/1-1s/[Name]/YYYY-MM-DD.md` |
| Partner name mentioned | SADP | `SADP/[topic].md` |
| Concepts, advisors, scripts repo | Jamf Concepts | `Jamf Concepts/[topic].md` |
| Claude, AI, MCP, agentic | Agentic Workflows | `Agentic Workflows/[topic].md` |
| FP, strategy, company | General | `Jamf Company Strategy/[topic].md` |
| Other | General | `Communications/[topic].md` |

---

## 1:1 Processing

Direct report 1:1s get special treatment:

1. **Template structure** - Consistent format across all 1:1s
2. **Named folder** - Each person has their own folder
3. **Date-based files** - Easy to find historical notes
4. **Bidirectional actions** - "Them" and "Me" columns

### Direct Reports

| Name | 1:1 Folder |
|------|-----------|
| Aaron Maxim | `CE Manager/1-1s/Aaron Maxim/` |
| Daniel MacLaughlin | `CE Manager/1-1s/Daniel MacLaughlin/` |
| Jonathan Yuresko | `CE Manager/1-1s/Jonathan Yuresko/` |
| Jedda Wignall | `CE Manager/1-1s/Jedda Wignall/` |
| Leslie Helou | `CE Manager/1-1s/Leslie Helou/` |
| Mark Buffington | `CE Manager/1-1s/Mark Buffington/` |
| Oliver Lindsey | `CE Manager/1-1s/Oliver Lindsey/` |
| Tim Knox | `CE Manager/1-1s/Tim Knox/` |

---

## Action Item Flow

### Extraction
- Look for commitments: "I'll", "Josh will", "action item", "TODO"
- Identify owner: Josh → "Me", others → their name
- Note any mentioned deadlines

### Things 3 Integration

Action items for Josh automatically go to Things 3:

1. **MCP server** (preferred) - Direct API access
2. **URL scheme** (fallback) - Opens Things and adds task

Task structure:
- **Title**: The action item text
- **Project**: Matches meeting category
- **Tags**: Category tag (SADP, CE Manager, etc.)
- **Notes**: Link to source summary file
- **Due date**: Only if explicitly mentioned

### Deduplication

After adding tasks, the skill checks for duplicates:
- Same title = potential duplicate
- Keep the one with a due date
- Remove others

---

## Troubleshooting

### "No transcripts found"

1. Check `_Pending Transcripts/` folder
2. Check `~/Documents/Zoom/` for recent folders
3. Verify Zoom is saving transcripts locally (Zoom settings)
4. Check folder watcher (see SETUP.md)

### Folder watcher not working

The folder watcher requires Full Disk Access:
1. System Settings → Privacy & Security → Full Disk Access
2. Add the watcher script or terminal app
3. See SETUP.md for detailed instructions

### Large transcript errors

Files over 25k tokens need chunked reading:
```
Read with offset=0, limit=500
Read with offset=500, limit=500
etc.
```

### Things 3 not receiving tasks

1. Check MCP server is running (restart Claude Code)
2. Try URL scheme fallback
3. Manually verify tasks were added

---

## Customization

### Adding new categories

1. Add pattern → category mapping in SKILL.md
2. Create target folder if needed
3. Add to category mapping table

### Changing template

Edit the 1:1 template section in SKILL.md. The canonical template lives at:
`CE Manager/1-1s/_template.md`

### Different task manager

Replace Things 3 integration section with your task manager's API or URL scheme.

---

## Credits

Built for Josh Sepos's daily workflow at Jamf. Designed around Zoom's transcript format and Things 3 task management.
