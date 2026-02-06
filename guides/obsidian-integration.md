# Using Claude Code with Obsidian

A guide to building a knowledge system where Claude Code and Obsidian work together as complementary tools for managers.

## The Mental Model

Think of your system as three layers:

```
┌─────────────────────────────────────────────────────────┐
│                    YOU (Human)                          │
│         Reading, reviewing, making decisions            │
└────────────────────────┬────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────┐
│                   OBSIDIAN                              │
│     Your window into the knowledge base                 │
│     • Browse and search                                 │
│     • Link ideas together                               │
│     • Review AI-generated content                       │
│     • Manual edits and annotations                      │
└────────────────────────┬────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────┐
│                  MARKDOWN FILES                         │
│     The actual knowledge base (folder on disk)          │
│     • Meeting notes and summaries                       │
│     • 1:1 histories                                     │
│     • Project docs                                      │
│     • Templates                                         │
└────────────────────────┬────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────┐
│                  CLAUDE CODE                            │
│     Your automated assistant working on the files       │
│     • Process transcripts → summaries                   │
│     • Extract action items → task system                │
│     • Gather context for prep                           │
│     • Answer questions about your data                  │
└─────────────────────────────────────────────────────────┘
```

**Key insight**: Obsidian and Claude Code both operate on the same markdown files, but serve different purposes:
- **Obsidian** = Human interface (reading, linking, navigating)
- **Claude Code** = Automation interface (processing, extracting, summarizing)

Neither replaces the other. They're complementary views into the same data.

---

## Information Flow

Here's how information moves through the system:

```
Raw Input                    Processing                    Output
─────────────────────────────────────────────────────────────────────

Meeting happens
      │
      ▼
┌─────────────┐
│ Transcript  │ ──────► Claude Code ──────► ┌─────────────────┐
│ (Zoom/Otter)│        processes it         │ Summary.md      │
└─────────────┘                             │ • Key points    │
                                            │ • Decisions     │
                                            │ • Action items  │
                                            └────────┬────────┘
                                                     │
                         ┌───────────────────────────┼───────────────┐
                         │                           │               │
                         ▼                           ▼               ▼
              ┌──────────────────┐      ┌─────────────────┐   ┌─────────────┐
              │  Task System     │      │   Your folder   │   │  Obsidian   │
              │  (Things 3, etc) │      │   structure     │   │  for review │
              │  • Your actions  │      │   (filed auto)  │   │             │
              └──────────────────┘      └─────────────────┘   └─────────────┘
```

### The Cycle

1. **Input arrives** (transcript, notes, email)
2. **Claude Code processes** it (summarize, extract, file)
3. **Files land** in your folder structure
4. **You review** in Obsidian
5. **Tasks appear** in your task system
6. **Context accumulates** for future queries

The more you use it, the more context Claude has. A 1:1 prep in month six draws on six months of conversation history.

---

## Suggested Folder Structure

Organize around **entities** (people, projects, partners), not **document types**.

### Why Entity-Centric?

```
❌ Document-type organization (harder to find things):
Notes/
├── meeting-notes/
│   ├── 2024-01-15-alex.md
│   ├── 2024-01-15-project-alpha.md
│   └── 2024-01-16-partner-call.md
├── 1-1-notes/
├── project-docs/
└── partner-docs/

✅ Entity-centric organization (everything about X is in X's folder):
Notes/
├── Team/
│   └── Alex/
│       ├── 1-1s/
│       │   ├── 2024-01-15.md
│       │   └── 2024-01-22.md
│       └── INDEX.md          ← Summary of Alex: role, goals, history
├── Projects/
│   └── Alpha/
│       ├── meeting_Kickoff_2024-01-10.md
│       ├── meeting_Weekly_2024-01-17.md
│       └── INDEX.md          ← Project summary: status, stakeholders
└── Partners/
    └── Acme/
        ├── meeting_Intro_2024-01-12.md
        └── INDEX.md          ← Partner summary: relationship, contacts
```

### Benefits of Entity-Centric

- **1:1 prep**: Claude reads `Team/Alex/` and has full context
- **Project status**: Claude reads `Projects/Alpha/` for everything relevant
- **Natural accumulation**: History builds up in one place per entity
- **Easy cleanup**: Archive an entire project folder when done

### The INDEX.md Pattern

Each entity folder gets an `INDEX.md` that serves as a summary/reference:

```markdown
# Alex Chen

## Role
Senior Engineer, Platform Team

## Current Focus
- Leading API redesign
- Mentoring two junior engineers

## Notes
- Prefers written feedback over verbal
- Career goal: architect track
- Started: March 2023

## Hot Topics
- Concerned about scope creep on Alpha project
- Wants more visibility into roadmap decisions
```

Claude reads these INDEX files during prep to understand current context without reading every historical file.

---

## Full Structure Example

```
WorkingContext/                    ← Your Obsidian vault
│
├── CLAUDE.md                      ← Instructions for Claude
├── INDEX.md                       ← Global quick reference
│
├── Team/                          ← Direct reports
│   ├── Alex/
│   │   ├── 1-1s/
│   │   │   ├── 2024-01-15.md
│   │   │   └── 2024-01-22.md
│   │   ├── feedback/
│   │   │   └── 2024-Q1-review.md
│   │   └── INDEX.md
│   ├── Jordan/
│   │   └── ...
│   └── _templates/
│       └── 1-1.md                 ← Template for 1:1 notes
│
├── Projects/                      ← Things you're tracking
│   ├── Alpha/
│   │   ├── meeting_Kickoff_2024-01-10.md
│   │   └── INDEX.md
│   └── Beta/
│       └── ...
│
├── Partners/                      ← External relationships
│   └── Acme/
│       └── ...
│
├── Stakeholders/                  ← Your manager, peers, skip-levels
│   ├── Pat-Director/
│   │   └── meeting_Weekly_2024-01-18.md
│   └── INDEX.md                   ← Who's who in leadership
│
├── _Inbox/                        ← Unprocessed/unsorted items
│   └── raw_transcript_2024-01-20.txt
│
├── _Archive/                      ← Completed/inactive items
│   └── Projects/
│       └── OldProject/
│
└── _Weekly/                       ← Weekly planning outputs
    └── 2024-W03.md
```

### Special Folders

| Folder | Purpose |
|--------|---------|
| `_Inbox/` | Drop zone for unprocessed items. Claude processes, then files appropriately. |
| `_Archive/` | Inactive items. Still searchable, but out of the way. |
| `_Weekly/` | Weekly planning snapshots. Useful for patterns over time. |
| `_templates/` | Reusable templates. Claude uses these when creating new files. |

The underscore prefix keeps utility folders sorted to the top/bottom (depending on your sort preference) and signals "system folder, not content."

---

## How Claude Code Connects

### The CLAUDE.md File

This file teaches Claude about your system:

```markdown
# My Working Context

## Folder Structure
- Team/[Name]/1-1s/ - 1:1 meeting notes
- Projects/[Project]/ - Project materials
- Partners/[Partner]/ - Partner communications

## Routing Rules
When processing a meeting transcript:
- 1:1 with direct report → Team/[Name]/1-1s/YYYY-MM-DD.md
- Project meeting → Projects/[Project]/meeting_Topic_YYYY-MM-DD.md
- Partner call → Partners/[Partner]/meeting_Topic_YYYY-MM-DD.md

## Direct Reports
- Alex Chen (Senior Engineer)
- Jordan Smith (Engineer)
- Sam Wilson (Junior Engineer)

## Task System
Using Things 3. Add my action items to the "Manager" project.
```

Claude reads this file automatically when you start a session in this folder.

### What Claude Can Do

With this setup, Claude can:

| Task | How It Works |
|------|--------------|
| "Process my transcripts" | Reads raw transcripts, creates summaries, files them, adds tasks |
| "Prep me for my 1:1 with Alex" | Reads `Team/Alex/`, surfaces recent context, suggests topics |
| "What's the status of Project Alpha?" | Reads `Projects/Alpha/`, synthesizes current state |
| "What did Jordan say about the deadline?" | Searches across meeting notes for relevant mentions |
| "Draft my weekly update" | Aggregates recent activity across all folders |

---

## Obsidian's Role

Obsidian is your **human interface** to this data:

### Navigation
- Use the file tree to browse by entity
- Quick search to find any mention of a topic
- Graph view to see connections (if you use wiki-links)

### Review
- Read Claude-generated summaries
- Edit and annotate where needed
- Add your own thoughts and context

### Linking (Optional)
- Use `[[wiki-links]]` to connect related notes
- Link people to projects they're involved in
- Build a knowledge graph over time

### Plugins to Consider
- **Dataview**: Query your notes programmatically
- **Calendar**: Navigate notes by date
- **Templates**: Quick-create from templates (though Claude handles most of this)

---

## The Workflow in Practice

### Morning Routine
```
1. Open Claude Code in your vault folder
2. "Check for pending transcripts"
   → Claude processes any new recordings
   → Summaries appear in appropriate folders
   → Action items added to your task system
3. Open Obsidian to review what was created
4. Start your day with context loaded
```

### 1:1 Prep (5 minutes before meeting)
```
1. "/1-1-prep Alex"
   → Claude reads Team/Alex/ folder
   → Surfaces: last 1:1 notes, any open items, INDEX context
   → Suggests: topics to cover, questions to ask
2. Walk into 1:1 with context fresh
```

### Weekly Planning (Sunday/Monday)
```
1. "/weekly-planning"
   → Claude looks at your task system
   → Checks your focus areas by day
   → Surfaces misalignments
   → Shows what's coming up
2. Adjust tasks, add prep reminders
3. Week starts with clarity
```

---

## Getting Started

### Minimum Viable Setup

1. **Create a folder** for your working context
2. **Add CLAUDE.md** with:
   - Your direct reports list
   - Basic folder structure
   - Routing rules for meeting notes
3. **Open in Obsidian** as a vault
4. **Run Claude Code** in that folder

You don't need the full structure on day one. Start with:
- One `Team/` folder with subfolders for each direct report
- A simple `CLAUDE.md`
- An `_Inbox/` for incoming items

Add complexity as patterns emerge.

### Growing the System

Over time:
- Add `INDEX.md` files as entities accumulate history
- Create templates for repeated structures
- Configure MCP servers for task integration
- Add skills for common workflows

The system compounds. Six months in, 1:1 prep draws on six months of context. That's when it gets powerful.

---

## Principles

### 1. Files Are the Source of Truth
Everything lives in markdown files on disk. Obsidian and Claude Code are just different ways to interact with those files. You can always switch tools without losing data.

### 2. Entity-Centric Over Document-Centric
Group by who/what, not by document type. "Everything about Alex" is more useful than "all 1:1 notes."

### 3. Progressive Complexity
Start simple. Add structure when you feel the need, not before. A working simple system beats an elaborate unused one.

### 4. Review What Claude Creates
Claude is fast but imperfect. Use Obsidian to review summaries, catch errors, and add nuance Claude missed. The human-in-the-loop improves quality and builds your understanding.

### 5. Context Compounds
Every meeting note, every 1:1 summary, every INDEX update adds to the context available for future queries. The system gets smarter the more you use it.
