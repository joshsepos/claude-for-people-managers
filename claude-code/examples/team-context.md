# CLAUDE.md Example: Team Context

Add this section to your CLAUDE.md to give Claude awareness of your team structure.

```markdown
## My Team

### Direct Reports
| Name | Role | Focus Areas |
|------|------|-------------|
| Alex Chen | Senior Engineer | Backend, APIs |
| Jordan Smith | Engineer | Frontend, mobile |
| Sam Wilson | Tech Lead | Architecture, mentoring |
| Casey Brown | Engineer | DevOps, infrastructure |

### 1:1 Schedule
| Day | Who |
|-----|-----|
| Tuesday | Alex, Jordan |
| Thursday | Sam, Casey |

Cadence: Fortnightly (odd weeks)

### Load Tracking
I track team capacity using this scale:
- 0 = Open for more work
- 1-2 = Light to steady
- 3 = Busy but manageable
- 4 = Stretched
- 5 = Overloaded, needs relief

### Team Notes Location
- 1:1 notes: `Team/[Name]/1-1s/`
- Individual context: `Team/[Name]/INDEX.md`
```

## Why This Helps

- **1:1 Prep**: Claude can find the right person's notes
- **Weekly Planning**: Claude knows when to create prep tasks
- **Context**: Claude understands your management scope

## Customization

Expand with additional context like:
- Each person's development goals
- Current projects per person
- Communication preferences
- Time zones if distributed
