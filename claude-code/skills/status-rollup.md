---
name: status-rollup
description: Generate a status summary for a project, partner, or initiative. Asks about depth (quick/standard/detailed) and puts blockers first. Use for meeting prep, stakeholder updates, or personal tracking.
argument-hint: [project or partner name]
---

# Status Rollup

Generate a status summary for a project, partner, or initiative.

## Configuration

**Update these for your setup:**

```yaml
# Your projects/partners to track
# Group them by category for easier routing

categories:
  projects:
    - name: "Project Alpha"
      aliases: ["Alpha", "alpha-project"]
      path: "~/Documents/Notes/Projects/Alpha/"
    - name: "Project Beta"
      aliases: ["Beta"]
      path: "~/Documents/Notes/Projects/Beta/"

  partners:
    - name: "Acme Corp"
      aliases: ["Acme"]
      path: "~/Documents/Notes/Partners/Acme/"
    - name: "Initech"
      path: "~/Documents/Notes/Partners/Initech/"

# Optional: Activity log location
activity_log: "~/Documents/Notes/log.md"

# Optional: Team index for people lookup
index_file: "~/Documents/Notes/INDEX.md"

# Task system
task_system: "things3"
```

## Workflow

### 1. Identify Target

Parse the argument:
- Match against known projects, partners, and aliases
- Route to the appropriate notes folder

### 2. Ask About Depth

Before gathering context, ask:

"What depth do you need?"
- **Quick** - 30-second summary (blockers + current phase only)
- **Standard** - Key info for a meeting (blockers + recent activity + next steps)
- **Detailed** - Full status report (everything including key docs and contacts)

### 3. Gather Context

**Always check:**
- Folder contents (all markdown files)
- Index file entry for this item
- Activity log (search for mentions)
- Task system (search by name)

**Only if user explicitly asks:**
- Jira/Linear for ticket status
- GitHub for code activity

### 4. Generate Output

**BLOCKERS FIRST** - This is the priority information.

#### Quick Format
```markdown
# [Name] - Quick Status

**Phase:** [Discovery | Development | Testing | Production | Maintenance]
**Blockers:** [List or "None identified"]
**Last activity:** [Date - one-liner]
```

#### Standard Format
```markdown
# [Name] - Status

**Phase:** [Phase]
**Priority:** [High | Medium | Low]

---

## Blockers / Risks
[List blockers - this comes FIRST]
- [Blocker 1]
- [Blocker 2]
[Or: "None identified"]

---

## Recent Activity
[Last 2-3 updates from log or recent files]
- [Date]: [Activity]

---

## Next Steps
1. [Immediate action]
2. [Following action]
```

#### Detailed Format
```markdown
# [Name] - Full Status Report
**Generated:** [Date]
**Type:** [Project | Partner | Initiative]

---

## Blockers / Risks
[FIRST - list all identified blockers]

---

## Current State
- **Phase:** [Phase]
- **Priority:** [Priority]
- **Last Activity:** [Date and description]

---

## Key People
| Role | Name |
|------|------|
| Owner | [Name] |
| Technical Lead | [Name] |
| Stakeholder | [Name] |

---

## Recent Activity
[Chronological list from log and recent files]

---

## Open Items
[From task system and docs]

---

## Key Documents
| Document | Purpose |
|----------|---------|
| [filename] | [description] |

---

## Next Steps
1. [Action]
2. [Action]
```

## Phase Definitions

Customize these to match your workflow:

| Phase | Meaning |
|-------|---------|
| Discovery | Exploring requirements, feasibility |
| Planning | Scoping, designing approach |
| Development | Active work in progress |
| Testing | Validation, QA |
| Production | Live, operational |
| Maintenance | Ongoing support, minor updates |
| On Hold | Paused, waiting on external factors |

## Tips

- Run before stakeholder meetings to have answers ready
- Use "Quick" for Slack responses
- Use "Detailed" for executive summaries or quarterly reviews
- Blockers first trains stakeholders to know you surface issues proactively
