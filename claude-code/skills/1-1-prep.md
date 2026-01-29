---
name: 1-1-prep
description: Prepare for a 1:1 meeting with a direct report. Gathers context from past 1:1s, parked topics, team index, and task management. Use when preparing for upcoming 1:1s or when asked "prep for my 1:1 with [name]"
argument-hint: [name]
---

# 1:1 Preparation

Prepare a brief for an upcoming 1:1 with a direct report.

## Configuration

**Update these for your setup:**

```yaml
# Your direct reports (first names for matching)
direct_reports:
  - name: "Alex Chen"
    first: "Alex"
  - name: "Jordan Smith"
    first: "Jordan"
  # Add your team members

# Path to your notes
base_path: "~/Documents/Notes"  # Change to your notes location

# 1:1 notes location pattern
one_on_one_path: "{base_path}/Team/{full_name}/1-1s/"

# Team index file (optional - for load/project info)
index_file: "{base_path}/INDEX.md"

# Task management
task_system: "things3"  # or "todoist", "linear", etc.
task_project: "Management"  # Project name for manager tasks
```

## Workflow

### 1. Identify the Person

- Accept first name or partial match
- Match to full name from your direct reports list
- If ambiguous or not a direct report, ask for clarification

### 2. Check for Past 1:1 Notes

Look in your configured 1:1 notes path for this person.

**If no 1:1 notes exist:**
- STOP and warn: "No past 1:1 notes found for [Name]. Would you like me to generate a brief from available context anyway, or create a first-1:1 template?"
- Wait for response before proceeding

**If notes exist:** Read the last 2-3 files (most recent first)

### 3. Gather Context

**From Past 1:1s** - Extract:
- Action items YOU committed to (PRIORITY - list these first)
- Action items THEY committed to
- Items explicitly parked for next time
- Key topics they raised
- Recent wins or blockers

**Parked Topics File** - Check for:
`{one_on_one_path}/parked-topics.md` or similar

**Team Index** - If available, extract:
- Current workload/capacity
- Current projects
- Development areas (for coaching awareness)

**Task System** - Search for:
- Tasks mentioning their name
- Tasks in your management project
- Any tasks where you owe them something

### 4. Generate Prep Brief

Output format - note "What I Owe Them" is FIRST:

```markdown
# 1:1 Prep: [Name]
**Date:** [Today's date]
**Last 1:1:** [Date of most recent 1:1]

---

## What I Owe Them
Action items I committed to in past 1:1s:
- [ ] [Item] - Status: [Done/Not done]
- [ ] [Item] - Status: [Done/Not done]

Tasks related to them:
- [ ] [Task from task system]

---

## What They Owe (Following Up)
- [ ] [Their action item from last 1:1]

---

## Parked Topics
[Items from parked topics file, or "None on file"]

---

## Their Current State
- **Load:** [Level if tracked]
- **Projects:** [Current work]
- **Recent context:** [Key topics from last 1:1]

---

## Flags (If Any)
[ONLY include this section if there's something notable:]
- Development area to weave in: [from index]
- Overdue item: [if something has been pending multiple 1:1s]
- Pattern noticed: [if same blocker keeps coming up]

[If nothing notable, omit this section entirely]
```

### 5. Output

Display the brief in the terminal. Do not save to file unless asked.

If asked to save, use your configured path pattern.

## Optional Integrations

### Calendar
If calendar integration available:
- Confirm the 1:1 is actually scheduled
- Note the meeting time in the prep brief
- Flag if the meeting was rescheduled or cancelled

### Task System MCP Servers
- **Things 3**: Use `mcp__things3__todos_list` with searchText
- **Linear**: Use Linear MCP tools
- **Todoist**: Use Todoist MCP tools

## Reference

**Load Scale Example:**
0=Open, 1=Light, 2=Steady, 3=Busy, 4=Stretched, 5=Maxed

Customize this scale to match your team's vocabulary.
