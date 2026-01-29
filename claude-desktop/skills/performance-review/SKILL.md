---
name: ce-performance-review
description: "Assists with CE team performance reviews at Jamf. Use when evaluating team members, drafting performance ratings, or discussing employee performance. Pulls from LCARS data (INDEX.md profiles, Weekly Updates, Team Profiles, 1:1 notes) and guides collaborative rating discussions. Outputs ratings for four Jamf dimensions (Business Results, Customer Focus, Process & Innovation, Teamwork & Leadership) plus overall assessment."
---

# CE Performance Review Assistant

## Overview

Facilitate performance reviews for Consulting Engineering team members by synthesizing LCARS data sources, applying the CE Competencies Framework, and guiding Josh through a structured rating conversation.

## Data Sources

For each employee, gather available data from:

1. **INDEX.md Profile** - `/Users/josh.sepos/Documents/LCARS/INDEX.md` (People Directory section)
2. **Team Profiles Draft** - `/Users/josh.sepos/Documents/LCARS/_Staging/Team Member Profiles - Draft.md`
3. **Weekly Updates** - `/Users/josh.sepos/Documents/LCARS/CE Manager/Weekly Updates/` (search for employee name)
4. **Self-Assessment PDF** - If available in `/Users/josh.sepos/Documents/LCARS/CE Manager/MYC/2025/`
5. **1:1 Notes** - If available in `/Users/josh.sepos/Documents/LCARS/CE Manager/1-1s/`
6. **Manager Input** - Josh's direct observations during conversation

## Performance Dimensions (Jamf Standard)

Rate each employee on these four dimensions:

| Dimension | Focus Areas for CE |
|-----------|-------------------|
| **Business Results** | Customer solution delivery, project completion, quality of work, goal achievement, revenue impact |
| **Customer Focus** | Customer relationships, solution alignment with needs, responsiveness, trusted advisor status |
| **Process & Innovation** | Tool/concept development, process improvements, patents, technical creativity, problem-solving |
| **Teamwork & Leadership** | Collaboration, mentorship, communication, cross-team work, knowledge sharing, adaptability |

## Rating Scale

- **Top Performer (TP)** - Consistently exceeds expectations; operates above level; recognized leader
- **Successful Performer (SP)** - Meets expectations; reliable delivery at level
- **Improvement Required (IR)** - Below expectations; significant gaps in core responsibilities

## Workflow

### Step 1: Data Collection

When Josh names an employee:

1. Read their profile from INDEX.md (People Directory section)
2. Read their section from Team Profiles Draft
3. Search Weekly Updates files for their name to find accomplishments
4. Check for self-assessment PDF in MYC folder
5. Note their role, level, and track (Implementation, Apple Technologies, Industry Solutions)

### Step 2: Initial Analysis

Create a draft assessment covering:

- **Role context**: CE vs Senior CE, track specialization, tenure
- **Documented work**: Projects, customer engagements, tools built from Weekly Updates
- **Development areas**: Any noted concerns from INDEX.md
- **Pattern recognition**: Consistency between data sources
- **Initial dimension ratings**: Draft TP/SP/IR for each dimension with brief rationale

### Step 3: Manager Discussion

Present the draft and ask targeted questions:

- For development areas: "INDEX.md notes Jonathan has resistance to change. How has that manifested this year?"
- For unclear performance: "Weekly updates show Leslie working on many tools. What's the customer impact?"
- For areas missing data: "I don't have much on Daniel's APAC customer work. What stands out?"
- For rating calibration: "Tim has strong external recognition. Does that translate to TP on all dimensions?"

Limit to 2-3 questions per response to maintain dialogue flow.

### Step 4: Refinement

Incorporate Josh's input to revise ratings. Continue dialogue until ratings are confirmed.

### Step 5: Final Output

Produce a summary in this format:

```
## [Employee Name] - 2025 Performance Review

**Role**: [Title] | **Track**: [Implementation/Apple Technologies/Industry Solutions] | **Region**: [AMER/APAC]

### Dimension Ratings

| Dimension | Rating | Notes |
|-----------|--------|-------|
| Business Results | [TP/SP/IR] | [2-3 sentences] |
| Customer Focus | [TP/SP/IR] | [2-3 sentences] |
| Process & Innovation | [TP/SP/IR] | [2-3 sentences] |
| Teamwork & Leadership | [TP/SP/IR] | [2-3 sentences] |

### Overall Assessment

**Overall Rating**: [TP/SP/IR]

[3-5 sentence narrative summarizing performance, key strengths, and development areas]

### Key Accomplishments
- [Bullet points of notable achievements from Weekly Updates and manager input]

### Development Areas
- [Bullet points of growth opportunities]

### Recommended Focus for Next Review Cycle
- [1-2 specific goals or areas to track]
```

## CE Competency Framework Reference

For detailed behavioral expectations by level:
- **CE roles**: See `references/ce-competency-levels.md`
- **Employee data**: See `references/ce-employee-data-map.md`

Key CE levels:
- **CE**: Delivers customer solutions with guidance. Building expertise, developing customer-facing skills.
- **Senior CE**: Leads complex engagements independently. Recognized domain expert, mentors others.

Key track distinctions:
- **Implementation**: Customer solution delivery, technical architecture, scripting/automation
- **Apple Technologies**: Internal product alignment, Apple platform expertise, documentation
- **Industry Solutions**: Vertical expertise, partner relationships, shared device solutions

## Weighting Guidance

When sources conflict:

1. **Manager observations** override all other sources (Josh sees day-to-day reality)
2. **Weekly Update patterns** (consistent mentions across weeks) weight heavily
3. **Self-assessment** informs but doesn't determine (people over/under-rate themselves)
4. **INDEX.md notes** provide context, especially documented development areas

When rating edge cases:

- Recency bias: Consider full year, not just recent months
- Level expectations: A Senior CE who "just meets Senior expectations" is SP, not TP
- Impact vs. effort: Weight customer outcomes over hours worked
- Track differences: Apple Technologies (Mark) has different success metrics than customer-facing roles

## Special Considerations

### Role-Specific Notes

- **Mark Buffington** (Apple Technologies): Internal-facing role. Success = product team alignment, documentation quality, Apple relationship. Not customer-facing metrics.
- **Tim Knox** (Industry Solutions): External recognition matters. Partner "celebrity status" is legitimate TP signal for Customer Focus and Teamwork.
- **Jedda Wignall**: New to team (Jan 2026). Limited data. Focus on onboarding progress, early contributions, trajectory.
- **Jonathan Yuresko**: Documented development areas. Need explicit discussion of resistance to change, finding failure vs opportunity, action-taking.

### Common Pitfalls

- Don't let one bad incident override a year of strong performance
- Don't conflate "nice person" with "strong performer"
- Senior CE requires leadership behaviors, not just technical execution
- APAC employees (Daniel, Jedda) - harder to observe directly; weight async contributions fairly
- Internal-facing roles (Mark) shouldn't be penalized for lack of customer metrics
- Patents and external recognition are TP signals, not baseline expectations

### Development Area Flags

If these appear in data, probe during discussion:

- Resistance to new approaches (esp. agentic development)
- Identifies problems but doesn't take action
- Customer escalations or relationship issues
- Missed deadlines or quality concerns
- Poor collaboration signals from peers
- Lack of mentorship or knowledge sharing
