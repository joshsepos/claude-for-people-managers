---
name: meeting-prep
description: Prepare for stakeholder meetings (not 1:1s with direct reports - use /1-1-prep for those). Gathers context, finds past meeting notes, and balances your agenda with theirs.
argument-hint: [attendee name(s) or meeting topic]
---

# Meeting Preparation

Prepare for meetings with stakeholders, partners, or cross-functional teams.

**Note:** For 1:1s with your direct reports, use `/1-1-prep` instead. This skill is for everyone else.

## Configuration

**Update these for your setup:**

```yaml
# Key stakeholders you meet with regularly
# This helps Claude understand context and find relevant notes

stakeholders:
  - name: "Pat Director"
    role: "Your manager"
    context: "Strategy, team direction, career"
    folder: "~/Documents/Notes/Skip-Level/"

  - name: "Alex Product"
    role: "Product Manager"
    context: "Roadmap, priorities, feature requests"
    folder: "~/Documents/Notes/Product/"

  - name: "Jordan Partner"
    role: "Partner Manager"
    context: "External relationships, contracts"
    folder: "~/Documents/Notes/Partners/"

# Where to search for past meeting notes
meeting_notes_paths:
  - "~/Documents/Notes/Meetings/"
  - "~/Documents/Notes/Communications/"

# Task system for open items
task_system: "things3"

# Team index for context
index_file: "~/Documents/Notes/INDEX.md"

# Save prep files here (optional)
prep_output_path: "~/Documents/Notes/_Meeting Prep/"
```

## Workflow

### 1. Identify Meeting Context

Parse the argument:
- **Who** - Match to stakeholder list or infer from name
- **Topic** - If provided, use it; otherwise infer from person's typical context

### 2. Find Past Meeting Notes

Search for previous meetings with this person:
- Check stakeholder-specific folder
- Grep meeting notes paths for their name
- Note the date and key points from the most recent meeting

### 3. Gather Current Context

**From your index file** - Read their entry and related projects

**From topic folders** - Based on person, check relevant project/initiative folders

**From task system** - Search for tasks related to them or the topic

### 4. Generate Prep Brief

Structured sections, balanced between your needs and theirs:

```markdown
# Meeting Prep: [Person/Topic]
**Date:** [Today]
**Attendees:** [Names]
**Last meeting:** [Date - or "First meeting" if none found]

---

## From Last Time
[Summary of previous meeting if found]
- Key decisions made
- Open items from then

---

## What I Need From Them
My agenda for this meeting:
1. [Decision or input needed]
2. [Question to ask]
3. [Update to request]

---

## What They'll Want From Me
Updates they'll likely ask about:
- [Topic] - [Current status]
- [Topic] - [Current status]

---

## Current Context
[Relevant background from index and topic folders]
- **Their focus:** [What they care about]
- **Hot topics:** [Current priorities]

---

## Open Tasks
Related items from task system:
- [ ] [Task]

---

## Watch For
[Any sensitivities or politics to be aware of]
```

## Stakeholder Categories

Different stakeholders need different prep focus:

| Category | Focus Areas |
|----------|-------------|
| Skip-level (your manager's manager) | Visibility, escalations, career growth |
| Peer managers | Coordination, shared resources, handoffs |
| Product/Design | Roadmap alignment, requirements, priorities |
| External partners/vendors | Deliverables, contracts, relationship health |
| Cross-functional leads | Dependencies, timelines, collaboration |

## Calendar Integration (Optional)

If calendar access available:
- Pull meeting details (time, attendees, agenda if set)
- Check for related calendar items the same day
- Note any recurring meeting history

## Save Prep File (Optional)

After generating, optionally save to your configured path:

**Location:** `{prep_output_path}/prep_[Person-Name]_YYYY-MM-DD.md`

Benefits of saving:
- Reference during the meeting
- Compare prep vs. actual meeting notes afterward
- Track patterns in what topics recur

---

## Tips

- For group meetings, prepare context for all attendees
- Check hot topics in your index before any meeting
- The "What They'll Want From Me" section prevents being caught off guard
- Update prep after meeting with what actually happened (for next time)
