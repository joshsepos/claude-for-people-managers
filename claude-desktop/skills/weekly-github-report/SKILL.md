---
name: weekly-github-report
description: "Generate activity reports for Jamf Concepts GitHub organization. Use when generating weekly reports, asking about Jamf Concepts activity this week, or saving the weekly report. Tracks PRs merged, open PRs, recent commits, open issues, and new repos across active repositories."
---

# Weekly GitHub Report Skill

## Trigger
- "Generate this week's Jamf Concepts report"
- "Jamf Concepts weekly report"
- "What happened in Jamf Concepts this week?"
- "Save the weekly report"

## Purpose
Generate activity reports for Jamf Concepts GitHub organization, tracking PRs, commits, issues, and contributors.

---

## Quick Method (Preferred)

A shell script exists for this. Use it when possible:

```bash
jamf-concepts-report          # Display report
jamf-concepts-report save     # Save to Weekly Reports folder
jamf-concepts-report 14       # Look back 14 days
```

If the command works, you're done. The script handles everything.

---

## Manual Method (If Script Unavailable)

### Configuration

| Setting | Value |
|---------|-------|
| GitHub Org | `Jamf-Concepts` |
| Local Repos | `/Users/josh.sepos/repos/jamf-concepts/` |
| Report Output | `Jamf Concepts/Weekly Reports/` |
| Default Lookback | 7 days |

### Active Repos (Focus On)

These repos get detailed attention:
- remote-remedy-backend
- RemoteRemedyEndpoint
- setup-checklist
- ddm-explorer
- mcp-examples
- apiutil
- wallpaper-designer
- jamf-compliance-editor
- remediaSOAR

### Report Sections

Generate a report with these sections:

#### 1. Header
```markdown
# Jamf Concepts Weekly Report
**Period**: [SINCE_DATE] to [TODAY]

---
```

#### 2. PRs Merged This Week
Query: `gh pr list --org Jamf-Concepts --state merged --search "merged:>=[SINCE_DATE]"`

Format:
```markdown
## PRs Merged This Week

- **[repo]**: [title] ([@author]) - [View](url)
```

#### 3. Open PRs (Awaiting Review)
Query: `gh pr list --org Jamf-Concepts --state open`

Format same as merged PRs.

#### 4. Recent Activity on Active Repos
For each active repo, show recent commits:

```bash
cd /Users/josh.sepos/repos/jamf-concepts/[repo]
git log --since="[SINCE_DATE]" --oneline --no-merges | head -10
```

Include contributors per repo.

#### 5. Open Issues Needing Attention
Query: `gh issue list --repo Jamf-Concepts/[repo] --state open`

Focus on active repos only.

#### 6. New Repos This Week
Query: `gh repo list Jamf-Concepts --limit 100 --json name,createdAt`

Filter to repos created since SINCE_DATE.

#### 7. Quick Stats
```markdown
---

## Quick Stats
- **Total repos in org**: [count]
- **Report generated**: [timestamp]
```

---

## Output Locations

| Action | Location |
|--------|----------|
| Display only | Stdout (default) |
| Save | `Jamf Concepts/Weekly Reports/report_Concepts-Weekly_YYYY-MM-DD.md` |

**Naming convention**: `[type]_[Topic-Name]_[date].md`

---

## Customization

### Changing Active Repos

Edit `ACTIVE_REPOS` in `/Users/josh.sepos/.local/bin/jamf-concepts-weekly-report.sh`

Or in SKILL.md, update the "Active Repos" list.

### Different Lookback Period

```bash
jamf-concepts-report 14   # 14 days
jamf-concepts-report 30   # 30 days
```

### Adding Sections

The script is at `/Users/josh.sepos/.local/bin/jamf-concepts-weekly-report.sh`. Add new sections there.

---

## Prerequisites

- `gh` CLI authenticated with GitHub
- Local repo clones at `/Users/josh.sepos/repos/jamf-concepts/`
- Repos should be up to date (auto-sync runs weekly via LaunchAgent)

### Sync Repos Manually
```bash
cd /Users/josh.sepos/repos/jamf-concepts && for d in */; do (cd "$d" && git pull --quiet); done
```

---

## Sample Output

```markdown
# Jamf Concepts Weekly Report
**Period**: 2026-01-14 to 2026-01-21

---

## PRs Merged This Week

- **setup-checklist**: Add retry logic for network failures (@armin) - [View](...)
- **ddm-explorer**: Update DDM schema for iOS 18 (@daniel) - [View](...)

## Open PRs (Awaiting Review)

- **remote-remedy-backend**: Chrome extension v2 (@josh) - [View](...)

## Recent Activity on Active Repos

### setup-checklist
```
a1b2c3d Add retry logic for network failures
d4e5f6g Update documentation
```
**Contributors**: armin, josh

### remote-remedy-backend
```
1234567 Add session timeout handling
8901234 Refactor tunnel management
```
**Contributors**: josh

**No activity**: wallpaper-designer, jamf-compliance-editor

## Open Issues Needing Attention

### ddm-explorer
- Support for macOS 15 DDM changes (@user) - [View](...)

## New Repos This Week

_No new repos created._

---

## Quick Stats
- **Total repos in org**: 46
- **Report generated**: 2026-01-21 15:30
```
