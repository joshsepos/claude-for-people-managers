---
name: pending-transcripts
description: "Process new Zoom meeting transcripts using the hybrid approach (chronological logs + thematic living docs). Use when processing transcripts, checking for pending transcripts, or asking about new transcripts. Handles _Pending Transcripts folder and ~/Documents/Zoom/ sources. Categorizes meetings, updates log.md files, updates thematic docs, and creates Things 3 tasks."
---

# Pending Transcripts Skill

## Trigger
- "Process my transcripts"
- "Check for pending transcripts"
- "Any new transcripts?"

## Purpose
Process new Zoom meeting transcripts using the **hybrid approach**: chronological logs + thematic living docs.

**Key principle:** No new meeting files. Content flows into `log.md` (chronology) and thematic docs (current state).

---

## Source Locations (Priority Order)

1. **Primary**: `_Pending Transcripts/` - Queued by folder watcher
2. **Fallback**: `~/Documents/Zoom/` - Look for transcript folders

### Zoom Folder Structure
```
~/Documents/Zoom/
└── YYYY-MM-DD HH.MM.SS Meeting Name/
    └── meeting_saved_closed_caption.txt
```

---

## Workflow

### Step 1: Find Transcripts

```
1. List _Pending Transcripts/ folder
2. If empty, check ~/Documents/Zoom/ for recent transcript folders
3. Skip if no transcripts found
```

### Step 2: Read & Categorize

For each transcript:

1. **Read the file**
2. **Identify meeting type** using categorization rules below
3. **Extract key information**:
   - Date (from filename or content)
   - Attendees (identify speakers)
   - Topics discussed
   - Decisions made
   - Action items (mark owner as "Me" for Josh's items)

### Step 3: Append to Log

Append a dated entry to the appropriate `log.md`:

```markdown
---

## YYYY-MM-DD - Meeting Title

**Attendees**: Names
**Topics**: Brief list of topics

### Key Points
- What was discussed
- Decisions made
- Notable context

**My action items**: List my tasks
**Threads updated**: [[thematic-doc-1]], [[thematic-doc-2]]
```

**Log file locations:**

| Category | Log File |
|----------|----------|
| 1:1 with direct report | `CE Manager/[Name]/log.md` |
| SADP partner meeting | `SADP/[Partner]/log.md` |
| SADP program-level | `SADP/_Program/log.md` |
| Jamf Concepts project | `Jamf Concepts/[Project]/log.md` |
| Jamf Concepts program | `Jamf Concepts/_Program/log.md` |
| Company strategy | `Jamf Company Strategy/log.md` |
| Agentic / AI tools | `Agentic Workflows/log.md` |
| Other | `Communications/log.md` |

**If log.md doesn't exist, create it** with a header:
```markdown
# [Category] - Meeting Log

Chronological record of [description].

---
```

### Step 4: Update Thematic Docs

Based on meeting content, update relevant thematic docs:

**For direct report 1:1s** - update these in `CE Manager/[Name]/`:

| Doc | Update Rule |
|-----|-------------|
| `current-focus.md` | Overwrite with their current projects/priorities |
| `projects.md` | Update status of projects they discussed |
| `career-development.md` | Append if career/growth topics discussed |

**For project meetings** - update these in `[Category]/[Project]/`:

| Doc | Update Rule |
|-----|-------------|
| `status.md` | Overwrite current state, update team table |
| `decisions.md` | Append any new decisions made |

**For company/program meetings** - update relevant thematic docs:

| Doc | Update Rule |
|-----|-------------|
| Topic-specific docs (e.g., `employee-engagement.md`) | Update with new info |
| Create new thematic doc if topic will recur | Only if 3+ meetings expected |

### Step 5: Cross-Reference (When Applicable)

If a meeting touches multiple domains, update all relevant docs:

**Example:** Aaron 1:1 discussing Remote Remedy
1. `CE Manager/Aaron Maxim/log.md` ← Full meeting entry
2. `CE Manager/Aaron Maxim/projects.md` ← Aaron's Remote Remedy status
3. `Jamf Concepts/Remote Remedy/status.md` ← Aaron's row in team table

### Step 6: Extract Action Items → Things 3

For action items assigned to Josh:
1. Add to Things 3 using MCP server (preferred) or URL scheme
2. **Project**: Match meeting category
3. **Tags**: Match category
4. **Due date**: ONLY if explicitly mentioned in meeting
5. **Notes**: Include `file://` link to the **thematic doc** (not log.md)

### Step 7: Archive Source

After successful processing:
1. Move the source transcript folder to `_Processed Transcripts/`
2. Confirm log entry and thematic docs updated

---

## Categorization Rules

| Keywords/Context | Category | Folder |
|-----------------|----------|--------|
| Direct report names (Aaron, Leslie, Jonathan, Daniel, Jedda, Oliver, Tim, Mark) | CE Manager | `CE Manager/[Name]/` |
| Partner names, Katie John, SADP, integration, partner manager, Matter Hub, intern training | SADP | `SADP/[Partner]/` or `SADP/_Program/` |
| Remote Remedy, remote access, VNC, SSH tunnel | Jamf Concepts | `Jamf Concepts/Remote Remedy/` |
| Fleet Health, AFHA, DEX, Dex, device health | Jamf Concepts | `Jamf Concepts/Fleet Health Analytics/` |
| Onboarder, Terraform, IAC, modular onboarder | Jamf Concepts | `Jamf Concepts/Modular Onboarder/` |
| Concepts governance, Advisors, intake | Jamf Concepts | `Jamf Concepts/_Program/` |
| AI, Claude, agentic workflows, MCP, automation patterns | Agentic Workflows | `Agentic Workflows/` |
| Company kickoff, FP, strategy, all-hands, manager summit | Jamf Company Strategy | `Jamf Company Strategy/` |
| Other meetings | Communications | `Communications/` |

---

## Direct Reports Reference

| Name | Role | 1:1 Day | Folder |
|------|------|---------|--------|
| Aaron Maxim | Senior CE - Implementation | Tuesday | `CE Manager/Aaron Maxim/` |
| Daniel MacLaughlin | Senior CE - Implementation | Tuesday | `CE Manager/Daniel MacLaughlin/` |
| Jonathan Yuresko | Senior CE - Implementation | Tuesday | `CE Manager/Jonathan Yuresko/` |
| Jedda Wignall | CE | Tuesday | `CE Manager/Jedda Wignall/` |
| Leslie Helou | CE - Implementation | Wednesday | `CE Manager/Leslie Helou/` |
| Mark Buffington | Senior CE - Apple Technologies | Wednesday | `CE Manager/Mark Buffington/` |
| Oliver Lindsey | Senior CE - Implementation | Thursday | `CE Manager/Oliver Lindsey/` |
| Tim Knox | Senior CE - Industry Solutions | Thursday | `CE Manager/Tim Knox/` |

---

## Thematic Doc Templates

### current-focus.md (for direct reports)
```markdown
# [Name] - Current Focus
*Last updated: YYYY-MM-DD*

## Active Projects
- **[Project]** - Role, current status

## Blockers
- [Any blockers mentioned]

## This Month
- [Key dates, deadlines, PTO]

## Looking Ahead
- [Career goals, upcoming work]
```

### projects.md (for direct reports)
```markdown
# [Name] - Active Projects

## [Project Name]
*Role*: Their role
*Status*: Current status
*Current*: What they're working on now
*Blockers*: Any blockers
*See also*: [[link to project status doc]]
```

### status.md (for projects)
```markdown
# [Project] - Status
*Last updated: YYYY-MM-DD*

## Current State
[Brief description of where project is]

## Team
| Person | Focus | Status |
|--------|-------|--------|
| [Name] | [Area] | [Status] |

## Recent Decisions
- YYYY-MM-DD: [Decision]

## Open Questions
- [Unresolved items]
```

---

## Things 3 Integration

**MCP Server**: Use things3-mcp if available

**Fallback URL Scheme**:
```
things:///add?title=TASK&notes=NOTES&tags=TAG&project=PROJECT
```

**Auth Token** (for updates): `3ZY_N2zbR5qsSsRYwGIKBg`

**Category → Project Mapping**:
| Category | Things 3 Project |
|----------|-----------------|
| SADP | SADP |
| Jamf Concepts | Jamf Concepts |
| CE Manager | CE Manager |
| Agentic Workflows | Agentic Workflows |
| Jamf Company Strategy | General |
| Other | General |

---

## Error Handling

### Transcript too large
- Use offset/limit parameters
- Read in chunks of 500 lines
- Or use Grep to find key sections

### Log file doesn't exist
- Create it with the standard header
- Then append the entry

### Thematic doc doesn't exist
- Create it using the template above
- Only create if topic is likely to recur

---

## Meeting Prep Comparison (When Available)

After processing a transcript, check for a matching prep file to generate a **meeting score**.

### Finding Prep Files

Look for prep files that match by:
1. **Person** - Same attendee name in filename
2. **Date proximity** - Prep file dated within 48 hours before the meeting

**Prep file pattern:** `prep_[Person-Name]_YYYY-MM-DD.md`

**Search locations:**
- `_Meeting Prep/prep_*.md` - Primary location for all prep files
- `CE Manager/[Name]/prep_*.md` - For direct report 1:1s (if prep used)

### Generating the Comparison

If a prep file is found, append a **Meeting Score** section to the log entry:

```markdown
### Meeting Score
*Prep file: [[prep_Person-Name_YYYY-MM-DD.md]]*

**Coverage (X/Y items):**
- [x] Topic I raised - Discussed
- [ ] Topic I planned - Not covered → carry forward

**Predictions:**
- [x] Expected them to ask about X - They did
- [ ] Expected them to ask about Y - They didn't

**Surprises:**
- They raised Z (not anticipated)

**Carryover to next meeting:**
- [ ] Topic not covered
- [ ] New item from this meeting
```

### Scoring Logic

| Metric | Calculation |
|--------|-------------|
| **Coverage** | Items from "What I Need From Them" that were discussed |
| **Prediction accuracy** | Items from "What They'll Want From Me" that came up |
| **Carryover** | Uncovered items + new action items for next prep |

### After Scoring

1. Update the prep file with a "Post-Meeting" section noting what was covered
2. Create action items for carryover topics
3. Flag patterns if recurring items keep getting missed (3+ times)

---

## Quality Checklist

Before marking complete:
- [ ] Transcript read and categorized correctly
- [ ] Log entry appended to correct `log.md`
- [ ] Relevant thematic docs updated (not created unnecessarily)
- [ ] Cross-references updated if meeting spanned multiple domains
- [ ] Action items extracted with correct owners
- [ ] Josh's items added to Things 3 with correct project/tags
- [ ] **Prep file checked** - If found, meeting score generated
- [ ] Source transcript moved to `_Processed Transcripts/`
