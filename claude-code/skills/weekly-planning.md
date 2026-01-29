---
name: weekly-planning
description: Plan the week by aligning tasks with focus areas (AOR days). Auto-moves misaligned tasks, creates 1:1 prep reminders, and shows the full week view. Best run Sunday evening or Monday morning.
---

# Weekly Planning

Review and organize the week. Aligns tasks with Area of Responsibility (AOR) days, flags overload, and creates 1:1 prep tasks.

## Configuration

**Update these for your setup:**

```yaml
# Your AOR schedule - what focus area for each day
aor_schedule:
  Monday:
    focus: "People Management"
    task_project: "Management"
  Tuesday:
    focus: "Project Alpha"
    task_project: "Alpha"
  Wednesday:
    focus: "External/Partners"
    task_project: "Partners"
  Thursday:
    focus: "Project Beta"
    task_project: "Beta"
  Friday:
    focus: "Admin/Flex"
    task_project: "General"

# Your 1:1 schedule (which day you meet with whom)
one_on_ones:
  Tuesday: ["Alex", "Jordan"]
  Thursday: ["Sam", "Casey"]

# 1:1 cadence
one_on_one_cadence: "fortnightly"  # or "weekly"

# Task system
task_system: "things3"  # or "todoist", "linear"

# Output location (optional)
weekly_plan_path: "~/Documents/Notes/_Weekly Plans/"
```

## Workflow

### 1. Get Current State

Fetch all relevant tasks from your task system:
- Today's tasks
- Upcoming/scheduled tasks
- Tasks by project

### 2. Auto-Align Tasks to AOR Days

For each task with a scheduled date:

**DO NOT MOVE if:**
- Task has a hard deadline
- Task is scheduled for today

**MOVE if misaligned:**
Check if the task's project matches the day's AOR. If not, move to the appropriate day.

Example logic:
| Task Project | Current Day | Should Be |
|--------------|-------------|-----------|
| Management | Not Monday | → Monday |
| Partners | Not Wednesday | → Wednesday |
| Alpha | Not Tuesday | → Tuesday |
| General | Any | → Friday (or leave flexible) |

Use bulk update tools where available.

### 3. Create 1:1 Prep Tasks

Check if this is a 1:1 week (based on cadence).

For each person with a 1:1 this week, check if a prep task already exists.

**If no prep task exists**, create one:
```
Title: "Prep for [Name] 1:1"
When: [day before their 1:1]
Project: "Management"
Notes: "Run /1-1-prep [Name]"
```

### 4. Analyze the Week

Calculate for each day:
- Number of tasks scheduled
- Any deadline-driven tasks
- Overload warning if >5 tasks on one day

Identify this week's deadlines.

### 5. Generate Full Week View

```markdown
# Week of [Date Range]
Generated: [Timestamp]

---

## Changes Made
- Moved X tasks to align with AOR days
- Created Y 1:1 prep tasks
- [List specific moves if any]

---

## Monday - [AOR Focus]
**Tasks:** [count]
- [ ] Task 1
- [ ] Task 2
[Flag if overloaded: ⚠️ Heavy day - consider deferring something]

---

## Tuesday - [AOR Focus]
**Tasks:** [count]
**1:1s this week:** [Names if applicable]
- [ ] Task 1
- [ ] Prep for [Name] 1:1 (if created)

---

[Continue for each day...]

---

## Deadlines This Week
| Task | Due | Project |
|------|-----|---------|
| [Task] | [Date] | [Project] |

---

## Flags
[Only if issues found:]
- ⚠️ [Day] is overloaded ([count] tasks)
- ⚠️ Deadline conflict: [Task] due [Date] but not scheduled
- ⚠️ No 1:1 notes for [Name] - first 1:1?
```

## Calendar Integration (Optional)

If calendar access available, pull events and show:
- **Tasks** (from task system)
- **Meetings** (from calendar)
- **Time available** = 8 hours - meeting hours

### Calendar Output Format

```markdown
## Monday - [AOR Focus]
**Tasks:** 3
**Meetings:** 4 (2.5 hrs)
**Available:** 5.5 hrs

### Meetings
- 9:00 AM - Team Standup (1 hr)
- 2:00 PM - Leadership Sync (1.5 hrs)

### Tasks
- [ ] Task 1
- [ ] Task 2
```

### Flags to Generate

| Condition | Flag |
|-----------|------|
| Meeting hours > 5 | ⚠️ Heavy meeting day |
| 1:1 scheduled but no prep task | ⚠️ Missing 1:1 prep |
| No meetings but many tasks | ✅ Focus day - protect it |

## Save Weekly Plan

After generating, optionally save to your notes:

**Location:** `{weekly_plan_path}/plan_YYYY-MM-DD.md`

This file becomes a living reference - update it as the week progresses.

---

## Notes

- Run this Sunday evening or Monday morning for best results
- Tasks without a scheduled date are listed as "Unscheduled" and not auto-moved
- Fortnightly 1:1 detection: check if current week number is odd/even based on your schedule
