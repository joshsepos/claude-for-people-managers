# Weekly Planning Workflow

Align your tasks with focus areas for the upcoming week.

## The Problem

Managers juggle multiple responsibilities: people management, project oversight, strategic work, administrative tasks. Without intentional planning:
- Important-but-not-urgent work gets perpetually deferred
- Context switching burns energy
- You end up reactive instead of proactive

## The Solution

Batch similar work together using "focus days" or themed time blocks:
1. Define your Areas of Responsibility (AORs) and assign them to days
2. Review your task list against these focus areas
3. Identify misalignments (tasks scheduled for wrong days)
4. Move tasks to appropriate days or flag conflicts
5. Surface the week ahead in a clear view

## Required Context

| Context | Purpose |
|---------|---------|
| AOR definitions | Your focus areas and their assigned days |
| Task system access | Read and update tasks (Things 3, Todoist, etc.) |
| Calendar (optional) | See meetings that might conflict with focus work |

## Example AOR Structure

```
Monday:    People Management (1:1 prep, team concerns, hiring)
Tuesday:   Project A (deep work on specific initiative)
Wednesday: Partner/External (stakeholder meetings, vendor work)
Thursday:  Project B (different initiative)
Friday:    Admin/Flex (catch-up, planning, misc)
```

## Inputs

- **Week start date** (optional): Defaults to upcoming Monday
- **Scope**: Just review, or actively move tasks?

## Outputs

- Tasks grouped by day with AOR alignment check
- Misaligned tasks flagged with suggested moves
- Heavy days identified (too many tasks)
- 1:1 prep reminders added for scheduled 1:1s
- Clean weekly view

## Implementation

- **Claude Code**: See `claude-code/skills/weekly-planning.md`
- **Claude Desktop**: See `claude-desktop/projects/weekly-planning.md`

## Customization Ideas

- Add calendar integration to see meetings per day
- Factor in energy levels (deep work mornings, admin afternoons)
- Include team member schedules for coordination
- Add recurring task generation (weekly reports, etc.)
