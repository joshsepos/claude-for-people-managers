# Interview Processor Skill

Process Zoom interview transcripts into structured evaluation summaries.

## When to Use This Skill

Use this skill when:
- Processing interview transcripts from Zoom recordings
- Creating candidate evaluation summaries
- Organizing interview notes for hiring decisions
- Building comparison views across multiple candidates

## Interview Summary Structure

### Header Section
```markdown
# [Candidate Name] - [Role/Program] Interview

**Date:** [Month Year]
**Interviewers:** [List of interviewers]
**Program/Role:** [MCRI, CE, etc.]

---
```

### Core Sections

1. **Candidate Overview** - 2-3 sentence summary of the candidate and their background

2. **Technical Background**
   - Programming languages/skills
   - Tools used (GitHub, Jira, etc.)
   - Notable projects with brief descriptions

3. **Interview Highlights** - Key moments organized by topic:
   - Approach to new/unfamiliar projects
   - Problem-solving when blocked
   - Team collaboration and conflict resolution
   - AI usage in workflow
   - Cross-timezone/async work experience
   - Career goals and aspirations
   - Ability to explain technical concepts

4. **Strengths** - Bulleted list of 5-8 key strengths observed

5. **Areas for Growth** - Bulleted list of 2-4 development areas

6. **Overall Assessment** - 1-2 paragraph synthesis with recommendation

### Footer
```markdown
---

#interview #[program] #[company] #[role-tag]
```

## Evaluation Categories

When analyzing interview transcripts, look for evidence in these areas:

### Technical Competence
- Programming language proficiency
- Tool familiarity (version control, project management)
- Problem decomposition approach
- Architecture/design thinking

### Communication Skills
- Clarity of explanations
- Ability to explain technical concepts to non-technical audiences
- Active listening (asking for clarification when needed)
- Professional demeanor

### Cultural Fit
- Alignment with company values/mission
- Collaboration style
- Feedback reception and giving
- Work environment preferences

### AI Proficiency
- How they use AI in development
- Prompting sophistication
- Awareness of AI limitations (hallucinations)
- Balance of AI assistance vs independent work

### Growth Mindset
- Response to challenges and failures
- Learning approach for new technologies
- Career development thinking
- Self-awareness about strengths/weaknesses

## Interview Question Patterns

Common questions to look for in transcripts:

| Question Type | What It Reveals |
|--------------|-----------------|
| "Approach to building something new" | Research habits, learning style, self-sufficiency |
| "Time you had to change direction" | Adaptability, decision-making under pressure |
| "Working across time zones" | Async communication, independence |
| "Conflict with teammates" | Conflict resolution, perspective-taking |
| "How do you use AI" | AI maturity, dependency vs tool usage |
| "Where do you see yourself in 2-3 years" | Career clarity, ambition |
| "Explain X to a non-technical person" | Communication skills, technical depth |

## Standout Indicators

Flag candidates who demonstrate:
- Wisdom beyond experience level (mark with #standout tag)
- Strong emotional intelligence
- Systems thinking (understanding interdependencies)
- Proactive problem-solving
- Genuine passion for helping others

## Output Locations

Save interview summaries to appropriate LCARS folders:

```
/LCARS/Interviews/
├── MCRI Interns/          # MCRI program candidates
├── Consulting Engineer/    # CE role candidates
└── [Role Name]/           # Other roles as needed
```

## Tips for Processing Transcripts

1. **Read full transcript first** - Get overall impression before note-taking
2. **Note interviewer reactions** - Comments like "impressive" or "great answer" indicate standout moments
3. **Quote sparingly** - Use quotes only for particularly memorable responses
4. **Balance objectivity** - Include both strengths and growth areas
5. **Consider context** - Experience level, program type, role requirements
6. **Look for red flags** - Over-reliance on AI, avoidance of questions, lack of self-awareness

## Comparison Format

When evaluating multiple candidates for the same role, create a comparison summary:

```markdown
# [Role/Program] Candidate Comparison

| Candidate | Technical | Communication | Cultural Fit | AI Usage | Standout? |
|-----------|-----------|---------------|--------------|----------|-----------|
| Name 1    | ⭐⭐⭐    | ⭐⭐⭐⭐       | ⭐⭐⭐⭐      | ⭐⭐⭐    | Yes       |
| Name 2    | ⭐⭐⭐⭐   | ⭐⭐⭐         | ⭐⭐⭐        | ⭐⭐⭐⭐   | No        |

## Summary
[Brief synthesis of how candidates compare]

## Recommendation
[Hiring recommendation with rationale]
```

## Integration with Existing Skills

This skill complements:
- **transcript-processor** - For non-interview meetings
- **pending-transcripts** - For processing new Zoom files
