# Weekly GitHub Report Skill - Documentation

## What This Does

Generates weekly activity reports for the Jamf-Concepts GitHub organization, tracking:
- PRs merged
- PRs awaiting review
- Recent commits on active repos
- Open issues needing attention
- New repos created
- Contributor activity

## Why It Exists

Josh oversees the Jamf Concepts program with 46+ repos. This report provides visibility into:
- What shipped this week
- What needs review
- Who's contributing
- Where to focus attention

---

## Two Ways to Run

### 1. Shell Command (Fastest)

```bash
jamf-concepts-report          # Display in terminal
jamf-concepts-report save     # Save to Weekly Reports folder
jamf-concepts-report 14       # 14-day lookback
```

### 2. Ask Claude

- "Generate this week's Jamf Concepts report"
- "What happened in Jamf Concepts repos this week?"
- "Save the weekly report"

Claude will either run the script or generate the report manually.

---

## Report Structure

### Sections Included

1. **PRs Merged** - Shipped work with author attribution
2. **Open PRs** - Work awaiting review
3. **Active Repo Activity** - Commits and contributors per repo
4. **Open Issues** - Items needing attention
5. **New Repos** - Newly created repos
6. **Quick Stats** - Total repo count, generation timestamp

### Active Repos (Focused Tracking)

Not all 46 repos get detailed tracking. These get special attention:

| Repo | Purpose |
|------|---------|
| remote-remedy-backend | HIGH PRIORITY - Remote access backend |
| RemoteRemedyEndpoint | HIGH PRIORITY - macOS agent |
| setup-checklist | User onboarding tool (Armin) |
| ddm-explorer | DDM learning tool |
| mcp-examples | AI/MCP integrations |
| apiutil | CLI for Jamf APIs |
| wallpaper-designer | iOS wallpaper tool |
| jamf-compliance-editor | Compliance config tool |
| remediaSOAR | SOAR integration |

---

## File Locations

| Item | Path |
|------|------|
| Wrapper script | `~/.local/bin/jamf-concepts-report` |
| Full script | `~/.local/bin/jamf-concepts-weekly-report.sh` |
| Saved reports | `Jamf Concepts/Weekly Reports/` |
| Local repo clones | `/Users/josh.sepos/repos/jamf-concepts/` |

---

## Prerequisites

### GitHub CLI

Must be installed and authenticated:
```bash
gh auth status  # Should show logged in
```

### Local Repo Clones

Reports pull commit data from local clones. Repos auto-sync weekly via LaunchAgent, but can be manually synced:

```bash
cd /Users/josh.sepos/repos/jamf-concepts
for d in */; do (cd "$d" && git pull --quiet); done
```

---

## Customization

### Adding/Removing Active Repos

Edit the `ACTIVE_REPOS` variable in:
`~/.local/bin/jamf-concepts-weekly-report.sh`

```bash
ACTIVE_REPOS="remote-remedy-backend setup-checklist ..."
```

### Changing Lookback Period

Default is 7 days. Override with argument:
```bash
jamf-concepts-report 14   # Two weeks
jamf-concepts-report 30   # One month
```

### Adding Report Sections

Edit the main script. Each section follows a pattern:
1. Query data (gh CLI or git)
2. Format as markdown
3. Echo to stdout

---

## Integration with Workflow

### Concept Advisors Meetings

Run before monthly Concept Advisors meetings to review activity.

### Status Updates

Use for weekly leadership updates - shows what the team shipped.

### Onboarding

Helps new team members see what's active and who's working on what.

---

## Troubleshooting

### "Command not found"

Check that `~/.local/bin` is in PATH:
```bash
echo $PATH | grep -o '.local/bin'
```

If missing, add to `~/.zshrc`:
```bash
export PATH="$HOME/.local/bin:$PATH"
```

### "No repos found" / Empty report

1. Check GitHub auth: `gh auth status`
2. Verify repo clones exist: `ls /Users/josh.sepos/repos/jamf-concepts/`
3. Run manual sync (see above)

### Stale data

Repos may be out of date. Run:
```bash
cd /Users/josh.sepos/repos/jamf-concepts && for d in */; do (cd "$d" && git pull --quiet); done
```

---

## Credits

Built for Jamf Concepts program management. Script uses `gh` CLI for GitHub API access and local git for commit history.
