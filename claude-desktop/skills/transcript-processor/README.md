# Transcript Processor - Documentation

## What This Does

Transforms raw meeting transcripts (Zoom recordings, audio transcriptions) into organized, consolidated knowledge base documents. Instead of 40 individual transcript summaries, you get ~10 topic-focused documents that combine related conversations.

## Why It Works This Way

### Consolidation > Individual Summaries

The naive approach: One summary per transcript = 40 summaries = chaos.

The better approach: Group related transcripts → consolidated topic documents:
- All SADP intern discussions → one "Intern Program" document
- Multiple Epic meetings → one "Epic Partnership" document
- Various Microsoft conversations → one "Microsoft Strategy" document

This gives you **searchable knowledge** instead of a pile of meeting notes.

### Categorization System

Built around Josh's actual work areas:

| Category | What Goes Here |
|----------|---------------|
| **SADP** | Partner integrations, Katie John meetings, partner manager work |
| **Jamf Concepts** | Community tools, Onboarder/Terraform, Concepts program governance |
| **CE Manager** | 1:1s, team management, performance, hiring |
| **Infrastructure** | Microsoft licensing, internal systems, demo environments |
| **Agentic Workflows** | AI adoption, Claude Code patterns, MCP work |
| **General** | Company strategy, FP syncs, all-hands |

### Speaker Identification

Transcripts often show "Speaker 1", "Speaker 2" without names. The skill uses context clues:
- Names mentioned in conversation
- Role references ("as the partner manager...")
- Technical vs non-technical speaking patterns
- Meeting title hints

---

## Folder Structure

```
Skills/transcript-processor/
├── SKILL.md              # Executable instructions (Claude reads this)
├── README.md             # This file (humans read this)
├── templates/
│   ├── sadp-partner.md   # Partner meeting template
│   ├── concepts-project.md
│   ├── one-on-one.md
│   ├── strategy.md
│   └── general.md
└── examples/
    └── (example outputs)
```

**Output location:**
```
_Staging/Transcripts Knowledge Base/
├── SADP/
├── Jamf Concepts/
├── CE Manager/
├── Infrastructure/
├── Agentic Workflows/
└── General/
```

---

## How to Use

### For Claude Code Users

Just say one of:
- "Process legacy transcripts"
- "Process transcripts from /path/to/folder"
- Reference the skill directly

Claude will read `SKILL.md` and follow the workflow.

### For Humans Setting This Up Elsewhere

1. **Copy the skill folder** to your project's Skills/ directory
2. **Modify categorization rules** in SKILL.md to match your work areas
3. **Customize templates** for your document types
4. **Update CLAUDE.md** to reference the skill (see example below)

#### CLAUDE.md Addition
```markdown
## Skills
| Skill | Trigger | Purpose |
|-------|---------|---------|
| transcript-processor | "Process transcripts" | Convert meeting transcripts to knowledge base |
```

---

## Key Patterns

### Handling Large Files

Zoom transcripts can be huge (50k+ tokens). The skill handles this:
1. Check file size first
2. Use offset/limit for chunked reading
3. Use Grep to find key sections in massive files

### Action Item Extraction

The skill extracts action items and:
- Marks Josh's items as "Me" (owner)
- Tags with appropriate category
- Adds to Things 3 via MCP or URL scheme
- Links back to source document

### Token Budget Management

When processing many files:
- Process in batches of 3-5 transcripts
- Create summaries as you go (don't hold everything in memory)
- Consolidate related topics into single documents to reduce total output

---

## Customization Guide

### Adding a New Category

1. Add to categorization table in SKILL.md
2. Create folder in staging structure
3. Optionally create a template in templates/

### Changing Output Format

Edit templates in `templates/` folder. Each template has:
- Standard header (date, category, attendees)
- Topic-specific sections
- Action items table
- Source reference

### Different Transcript Sources

The skill assumes Zoom-style transcripts with timestamps and speaker labels. For other formats:
- Adjust speaker identification logic
- Modify timestamp parsing
- Update template source references

---

## Troubleshooting

### "File exceeds token limit"
Use offset/limit parameters or Grep to read portions.

### Transcripts not categorizing correctly
Check keyword matching in categorization rules. Add new keywords as needed.

### Missing speakers
Some transcripts just don't have enough context. Mark as "Unknown" and move on.

### Duplicate content
If same meeting recorded multiple times, consolidate and note in summary.

---

## Example Output

See `examples/` folder for sample consolidated documents showing:
- Multiple source transcripts combined
- Speaker identification
- Action item extraction
- Template usage

---

## Credits

Developed for Josh Sepos's LCARS knowledge management system, January 2026.

Patterns applicable to any meeting-heavy role needing to convert conversations into searchable knowledge.
