---
name: transcript-processor
description: "Process bulk/legacy meeting transcripts into chronological logs and thematic living docs. Use when processing transcripts from a folder, handling legacy transcripts, or running /process-transcripts. Categorizes meetings into SADP, Jamf Concepts, CE Manager, Agentic Workflows, and other domains. Outputs log entries to appropriate log.md files and updates thematic docs."
---

# Transcript Processor Skill

## Trigger
- "Process legacy transcripts"
- "Process transcripts from [folder]"
- "/process-transcripts"

## Purpose
Process bulk/legacy meeting transcripts using the **hybrid approach**: chronological logs + thematic living docs.

**Key principle:** No new meeting files per transcript. Content flows into `log.md` (chronology) and thematic docs (current state). Group related transcripts to build consolidated knowledge.

## Input
- Source folder containing `.md` or `.txt` transcript files
- Default: `/Users/josh.sepos/Documents/Transcripted/`

## Output
- Log entries appended to appropriate `log.md` files
- Thematic docs created/updated in production folders
- Action items added to Things 3

---

## Workflow

### Phase 1: Discovery

1. List source folder contents, note file sizes
2. Identify named files (easier to categorize) vs unnamed "New Recording" files
3. Group files by apparent topic/category before processing
4. Plan which log files and thematic docs will be affected

### Phase 2: Categorization

Use these rules to categorize transcripts:

| Keywords/Context | Category | Log File |
|-----------------|----------|----------|
| Partner names (SentinelOne, Epic, Splunk, etc.), Katie John, SADP, integration, partner manager, Matter Hub | SADP | `SADP/_Program/log.md` or `SADP/[Partner]/log.md` |
| Concepts governance, Advisors, intake process, evaluation | Jamf Concepts | `Jamf Concepts/_Program/log.md` |
| Remote Remedy, remote access, VNC, SSH tunnel | Jamf Concepts | `Jamf Concepts/Remote Remedy/log.md` |
| Fleet Health, AFHA, DEX, Dex, device health | Jamf Concepts | `Jamf Concepts/Fleet Health Analytics/log.md` |
| Onboarder, Terraform, IAC, modular onboarder | Jamf Concepts | `Jamf Concepts/Modular Onboarder/log.md` |
| Experience Jamf, EJ, demo app | Jamf Concepts | `Jamf Concepts/Experience Jamf/log.md` |
| MCP, Model Context Protocol, AI integrations | Jamf Concepts | `Jamf Concepts/MCP/log.md` |
| 1:1, direct report names, performance, MYC | CE Manager | `CE Manager/[Name]/log.md` |
| AI, Claude, agentic workflows, automation patterns | Agentic Workflows | `Agentic Workflows/log.md` |
| Company kickoff, FP, strategy, all-hands | Jamf Company Strategy | `Jamf Company Strategy/log.md` |
| Other meetings | Communications | `Communications/log.md` |

### Phase 3: Processing

For each transcript:

1. **Read the file** (use offset/limit for files >25k tokens)
2. **Identify speakers** based on context clues
3. **Extract key information**:
   - Date and attendees
   - Main topics discussed
   - Decisions made
   - Action items (mark owner as "Me" for Josh's items)
4. **Categorize** using rules above

### Phase 4: Update Logs

For each transcript, append an entry to the appropriate `log.md`:

```markdown
---

## YYYY-MM-DD - Meeting Title

**Attendees**: Names
**Topics**: Brief list

### Key Points
- What was discussed
- Decisions made
- Notable context

**My action items**: List my tasks
**Threads updated**: [[thematic-doc-1]], [[thematic-doc-2]]
```

**If log.md doesn't exist, create it** with header:
```markdown
# [Category] - Meeting Log

Chronological record of [description].

---
```

**Sort entries** by date (most recent first) after appending.

### Phase 5: Create/Update Thematic Docs

**DO NOT create one doc per transcript.** Instead:

1. Group insights from related transcripts
2. Create/update thematic docs that consolidate knowledge:

**For projects:**
| Doc | Purpose | Update Rule |
|-----|---------|-------------|
| `status.md` | Current state, team, recent decisions | Overwrite with latest state |
| `decisions.md` | Architectural/strategic decisions | Append new decisions |

**For people (CE Manager):**
| Doc | Purpose | Update Rule |
|-----|---------|-------------|
| `current-focus.md` | What they're working on now | Overwrite |
| `projects.md` | Their project involvement | Update project entries |
| `career-development.md` | Growth discussions | Append if relevant |

**For programs:**
| Doc | Purpose | Update Rule |
|-----|---------|-------------|
| Topic-specific docs | Consolidated knowledge on recurring topics | Update with new info |

### Phase 6: Cross-References

When a transcript spans multiple domains:

1. Add log entry to primary category
2. Update thematic docs in both domains
3. Link between docs where helpful

**Example:** Aaron 1:1 about Remote Remedy
- Log entry → `CE Manager/Aaron Maxim/log.md`
- Update → `CE Manager/Aaron Maxim/projects.md` (his view)
- Update → `Jamf Concepts/Remote Remedy/status.md` (project view)

### Phase 7: Action Items

For any action items assigned to Josh ("Me"):
1. Add to Things 3 using MCP server or URL scheme
2. **Project**: Match category
3. **Tags**: Match category
4. **Notes**: Link to thematic doc (not log.md)
5. **Due date**: Only if explicitly mentioned

---

## Thematic Doc Templates

### status.md (for projects)
```markdown
# [Project] - Status
*Last updated: YYYY-MM-DD*

## Current State
[Brief description]

## Team
| Person | Focus | Status |
|--------|-------|--------|
| [Name] | [Area] | [Status] |

## Recent Decisions
- YYYY-MM-DD: [Decision]

## Open Questions
- [Unresolved items]
```

### decisions.md (for projects)
```markdown
# [Project] - Decisions

Architectural and strategic decisions made over time.

---

## YYYY-MM-DD - [Decision Title]
**Context**: Why this came up
**Decision**: What was decided
**Rationale**: Why this approach
**Alternatives considered**: What else was discussed
```

### current-focus.md (for people)
```markdown
# [Name] - Current Focus
*Last updated: YYYY-MM-DD*

## Active Projects
- **[Project]** - Role, status

## Blockers
- [Any blockers]

## This Month
- [Key dates, deadlines]

## Looking Ahead
- [Upcoming work, goals]
```

---

## Token Management

Large files (>25k tokens) require chunked reading:
```
Read file with offset=0, limit=500 (first 500 lines)
Read file with offset=500, limit=500 (next 500 lines)
```

For very large files (>50k tokens), use Grep to find key sections first.

---

## Quality Checklist

Before marking complete:
- [ ] All transcripts categorized correctly
- [ ] Log entries added to appropriate `log.md` files
- [ ] Thematic docs created/updated (consolidated, not 1:1 per transcript)
- [ ] Cross-references in place for multi-domain meetings
- [ ] Speakers identified where possible
- [ ] Action items extracted and added to Things 3
- [ ] Source files moved to `_Processed Transcripts/`

---

## Post-Processing

After processing complete:
1. User reviews output in Obsidian
2. Verify thematic docs capture key knowledge
3. Move processed source files to `_Processed Transcripts/`
