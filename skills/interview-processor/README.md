# Interview Processor Skill

A Claude skill for processing Zoom interview transcripts into structured candidate evaluation summaries.

## Purpose

Transforms raw interview transcripts into actionable hiring documentation:
- Individual candidate evaluation summaries
- Side-by-side candidate comparisons
- Consistent evaluation criteria across interviews

## When to Use

- Processing interview recordings from Zoom
- Creating candidate evaluations for hiring decisions
- Building comparison views across multiple candidates for the same role
- Documenting interview feedback for hiring committees

## Features

- **Structured summaries** with consistent sections (overview, technical background, highlights, strengths, growth areas, assessment)
- **Evaluation framework** covering technical competence, communication, cultural fit, AI proficiency, and growth mindset
- **Comparison tables** for evaluating multiple candidates
- **Standout flagging** for exceptional candidates

## File Structure

```
interview-processor/
├── README.md           # This file
├── SKILL.md            # Main skill instructions
├── templates/
│   ├── intern.md       # Template for intern interviews
│   ├── individual-contributor.md  # Template for IC roles
│   └── comparison.md   # Template for candidate comparisons
└── examples/
    └── mcri-intern-example.md  # Example output
```

## Usage

Invoke this skill when processing interview transcripts:

```
Process the interview transcript and create a candidate evaluation summary
```

The skill will guide Claude to:
1. Extract key information from the transcript
2. Evaluate against standard criteria
3. Generate a structured summary
4. Save to the appropriate LCARS location

## Integration

Works alongside:
- `transcript-processor` - For general meeting transcripts
- `pending-transcripts` - For processing new Zoom files

## Output Locations

Summaries are saved to:
```
/LCARS/Interviews/
├── MCRI Interns/       # Intern program candidates
├── Consulting Engineer/ # CE role candidates
└── [Role Name]/        # Other roles as needed
```
