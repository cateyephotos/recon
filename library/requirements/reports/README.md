---
ai_description: |
  Contains routine code-scan, QA, and security reports NOT tied to any
  specific PRD or IRD. Naming: <YYYY-MM-DD>-<type>-report.md.
  Authored by your QA reviewer or your security reviewer.
  Do NOT put per-PRD QA reports here: those go in prd-<###>-<slug>/qa/.
  Do NOT put IRD QA reports here: those go in ird-<###>-<slug>/qa/.
human_description: |
  Routine scan and audit reports not tied to a specific PRD or IRD.
  Examples: weekly security scans, periodic QA sweeps, dependency audits.
  Naming: 2026-05-23-security-scan-report.md, 2026-06-01-qa-sweep-report.md.
  Per-PRD QA reports live inside the PRD folder's qa/ subfolder instead.
---

# Requirements: Reports

Routine repository scan and audit reports not tied to any specific PRD. QA and security reviewers author the report content; Library owns only the scaffold.

Recon research outputs instead belong in `recon-reports/` in the invoking project, per [`skills/recon/SKILL.md`](../../../skills/recon/SKILL.md). Do not move those outputs here.

## Naming

`<YYYY-MM-DD>-<type>-report.md`

Examples:
- `2026-05-23-security-scan-report.md`
- `2026-06-01-qa-sweep-report.md`
- `2026-06-15-dependency-audit-report.md`

## What does NOT belong here

- QA reports for a specific PRD → `requirements/<lifecycle>/prd-<###>-<slug>/qa/`
- QA reports for a specific IRD → `issues/<lifecycle>/ird-<###>-<slug>/qa/`

`<lifecycle>` is the plan's current `backlog`, `in-work`, or `completed` folder. Keep the plan and its QA history together.
