# Performance Review Skill - Documentation

## What This Does

Facilitates CE team performance reviews by synthesizing data from multiple LCARS sources, applying Jamf's performance framework, and guiding a structured rating conversation.

## Why It Works This Way

### Multi-Source Data Synthesis

Performance reviews shouldn't rely on memory alone. This skill pulls from:

1. **INDEX.md Profile** - Role, level, development areas, relationships
2. **Team Profiles Draft** - Detailed competencies and work history
3. **Weekly Updates** - Documented accomplishments over time
4. **Self-Assessments** - Employee perspective (PDFs in MYC folder)
5. **1:1 Notes** - Ongoing conversation history
6. **Manager Input** - Josh's direct observations (most important)

### Structured Dialogue Over Automated Ratings

The skill doesn't just spit out ratings - it:
1. Gathers data
2. Creates draft assessment
3. Asks targeted questions
4. Refines based on manager input
5. Produces final output

This ensures human judgment drives final ratings while AI handles synthesis.

---

## Jamf Performance Framework

### Four Dimensions

| Dimension | CE Focus |
|-----------|----------|
| **Business Results** | Customer delivery, project completion, goal achievement |
| **Customer Focus** | Relationships, responsiveness, trusted advisor status |
| **Process & Innovation** | Tool development, process improvements, creativity |
| **Teamwork & Leadership** | Collaboration, mentorship, knowledge sharing |

### Rating Scale

- **Top Performer (TP)** - Exceeds expectations, operates above level
- **Successful Performer (SP)** - Meets expectations at level
- **Improvement Required (IR)** - Below expectations, significant gaps

---

## How to Use

### Trigger
Say one of:
- "Let's do a performance review for [Name]"
- "Performance review for Aaron"
- "Help me evaluate Leslie"

### What Happens
1. Claude reads all available data sources
2. Presents draft assessment with initial ratings
3. Asks 2-3 targeted questions
4. Refines ratings based on your input
5. Produces final structured output

### Expected Output

```markdown
## [Name] - 2025 Performance Review

**Role**: [Title] | **Track**: [Track] | **Region**: [Region]

### Dimension Ratings
| Dimension | Rating | Notes |
|-----------|--------|-------|
| Business Results | SP | [rationale] |
| Customer Focus | TP | [rationale] |
...

### Overall Assessment
[Narrative summary]

### Key Accomplishments
- [bullets]

### Development Areas
- [bullets]
```

---

## Special Considerations

### Role-Specific Notes

Different roles need different evaluation lenses:

| Person | Consideration |
|--------|---------------|
| **Mark Buffington** | Internal-facing (Apple Technologies). Don't use customer metrics. |
| **Tim Knox** | External recognition matters. Partner "celebrity status" is TP signal. |
| **Daniel/Jedda** | APAC - harder to observe directly. Weight async contributions. |
| **Jonathan** | Documented development areas. Probe resistance to change. |

### Weighting When Sources Conflict

1. **Manager observations** override all (you see day-to-day reality)
2. **Weekly Update patterns** (consistent mentions across weeks) weight heavily
3. **Self-assessment** informs but doesn't determine
4. **INDEX.md notes** provide context

### Common Pitfalls

- Don't let one bad incident override a year of strong performance
- "Nice person" ≠ "strong performer"
- Senior CE requires leadership, not just technical execution
- Patents/external recognition are TP signals, not baseline expectations

---

## File Structure

```
Skills/performance-review/
├── SKILL.md           # Claude's instructions
├── README.md          # This file (human documentation)
└── references/
    ├── ce-competency-levels.md   # Behavioral expectations by level
    └── ce-employee-data-map.md   # Where to find data per employee
```

---

## Customization

### Adding New Team Members

Update these locations:
1. INDEX.md - People Directory section
2. `references/ce-employee-data-map.md` - data source locations
3. SKILL.md - Special Considerations section if role-specific notes needed

### Changing Dimensions

Edit the Performance Dimensions table in SKILL.md. This is Jamf's standard framework - changes should align with HR guidance.

### Different Review Cycles

The skill defaults to annual reviews. For MYC (mid-year check-ins), note that ratings are typically more formative than summative.

---

## Credits

Built for Josh Sepos's CE team at Jamf. Designed around Jamf's four-dimension performance framework and CE competency expectations.
