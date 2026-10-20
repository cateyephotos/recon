---
ai_description: |
  Canonical Library Schema v2 for a repository. Use this file to decide where
  PRDs, IRDs, knowledge, ADRs, reports, and human notes belong. Lifecycle is
  represented by folder location. Never read or write library/notes/ as an AI.
human_description: |
  The rules for organizing repository planning and knowledge. Read this when
  you are unsure where a document belongs or when a PRD or IRD changes state.
---

# Recon Documentation Framework

Library Schema v2 organizes Recon's source-backed explanations, product plans, and issue plans. Recon is a Markdown agent skill, not an application.

Version: **2.0**
Updated: **2026-10-19**

## Repository source and scope

The implementation is [`skills/recon/SKILL.md`](../../../../skills/recon/SKILL.md). Its YAML frontmatter exposes `/recon` to a host agent; the Markdown defines argument handling, research phases, compliance modules, and report contracts. `/recon` is not a shell executable. The checkout has no application runtime, dependency manifest, test suite, or build/deploy pipeline. Do not infer those from inherited Python project context or from examples describing research targets.

The [workflow narrative](../architecture/recon-workflow.md) and [usage guide](../operations/recon-usage.md) have separate narrative ownership. Cite the skill's section or line range for behavioral claims, and refresh citations when the source changes. Preserve documented ambiguities instead of silently resolving them in scaffold text.

Recon writes research reports under `recon-reports/` in the invoking project (source: `skills/recon/SKILL.md:126-171`). Those are distinct from this Library's repository QA evidence. Initializing the Library does not execute research, validate compliance, or demonstrate host-agent behavior.

## Wiki and graph coverage

The user approved a partial wiki with documented graph limitations. Narrative Markdown can explain the skill, but does not establish extracted functions, types, call edges, runtime dependencies, or complete symbol coverage. No tree-sitter extraction or graph generation is performed by this scaffold task. Do not describe manually documented workflow relationships as a verified code dependency graph.

The `library/knowledge/private/codebase-graph/` subtree is separately owned. Leave its contents and graph-driver global `index.md`, `log.md`, `hot.md`, and hash files untouched. Consult that owner's evidence for actual graph coverage; absence of symbol output is not evidence of completeness.

Authored wiki pages live in `library/knowledge/` alongside narrative docs. Keep separate file ownership and never rewrite another author's output during scaffolding. If a page's backing source disappears, flag it for its owner rather than deleting it. No automatic wiki sync, external mirror, hooks, providers, or services are configured by this initialization. Any future generated mirror is derived and must be regenerated from its sources.

## Top-level map

```text
library/
  knowledge/
    public/
    private/
  requirements/
    backlog/
    in-work/
    completed/
    reports/
  issues/
    backlog/
    in-work/
    completed/
  notes/
```

| Folder | What belongs there | What does not belong there |
| --- | --- | --- |
| `knowledge/public/` | End-user guides, public overviews, and FAQs | Private architecture, security details, or product plans |
| `knowledge/private/` | Architecture, ADRs, engineering standards, and internal explanations | Active product requirements or bug-fix plans |
| `requirements/` | Product and feature work written as PRDs | Reactive bugs and incidents |
| `issues/` | Reactive work written as IRDs and tied to GitHub issue numbers | Planned features |
| `notes/` | Human-only scratch material | Anything authoritative or anything an AI agent should read |

## Knowledge documents

Most knowledge files explain what is true now. Accepted shared contract records are the exception: they record exact behavior that multiple PRDs have agreed to build against.

Use `knowledge/public/` only for information approved for external readers. Use `knowledge/private/` for internal engineering, business, security, or architecture material. When unsure, start in `private/`. This is an audience boundary, not access control: do not place secrets or confidential research in a publicly accessible checkout.

Architecture Decision Records live at:

```text
library/knowledge/private/architecture/ADR-<number>-<kebab-slug>.md
```

An ADR records one important decision, its context, alternatives, and consequences. It does not replace a PRD.

Accepted shared interface agreements live at `library/knowledge/private/contracts/CTR-<###>-<slug>.md`. The contract-writing Drone owns their terms and revisions. PRDs pin an accepted revision under a `## Contract dependencies` heading; a Draft contract leaves affected implementation work blocked. The record stays in place while PRD folders move.

## Product Requirements Documents

A PRD is a build blueprint and an inspection checklist for planned product work. New PRDs always begin in `requirements/backlog/`.

```text
library/requirements/backlog/prd-<###>-<slug>/
  prd-<###>-<slug>-index.md
  prd-<###>a-<slug>-<feature>.md
  qa/
```

Rules:

1. List all `prd-*` folders across `backlog/`, `in-work/`, and `completed/`; take the maximum number plus one, starting at `001` if none exist. Use three-digit zero padding, or natural width for four or more digits. Never reuse a number.
2. Keep the index and every sub-PRD inside one `prd-<number>-<slug>/` folder.
3. Write testable acceptance criteria. A reviewer must be able to answer pass or fail from evidence.
4. Create the PRD in `backlog/`, move the entire folder to `in-work/` when implementation begins, then move it to `completed/` only after the work ships and verification passes.
5. Treat `completed/` as read-only history. Correct a shipped requirement with a new PRD or an explicitly documented amendment process.
6. Before splitting work across independent PRDs, identify shared boundaries and pin the accepted contract revision in each affected PRD.

## Issue Requirements Documents

An IRD is a focused fix plan for a bug, incident, or other reactive issue. Its number matches the GitHub issue number.

```text
library/issues/backlog/ird-042-stale-cache/
  ird-042-stale-cache-index.md
  qa/
```

Rules:

1. Create the GitHub issue first.
2. Use that issue number in the IRD folder and index filename.
3. Keep an IRD single-scope. Do not create sub-IRDs.
4. Move the entire folder from `backlog/` to `in-work/` when the fix begins, then to `completed/` after the issue is closed and the fix is verified.

## Reports and QA evidence

Evidence tied to a PRD or IRD stays inside that document's `qa/` folder. This keeps the plan and proof together.

Routine repository-wide reports that are not tied to one PRD or IRD live in:

```text
library/requirements/reports/<YYYY-MM-DD>-<type>-report.md
```

Examples include a periodic security scan, repository-health audit, or general QA sweep. QA and security reviewers own those findings; Library owns the scaffold, not QA content.

## Human notes

`library/notes/` is a human-only scratch area. AI agents must not read it, write it, summarize it, or cite it. Notes are not authoritative. When a note becomes durable knowledge, a human moves or rewrites it into the appropriate `knowledge/` path.

## Document frontmatter

Every seeded folder README uses two descriptions:

- `ai_description` tells an AI what it may do in the folder.
- `human_description` gives a quick plain-language explanation.

Content documents may add fields such as status, version, owner, and updated date when the team's workflow requires them. Do not invent metadata that nobody maintains.

## Naming rules

- Use lowercase kebab-case for folders and ordinary knowledge files.
- Use `prd-<###>-<slug>` for PRD folders.
- Use `ird-<issue-number>-<slug>` for IRD folders.
- Use `ADR-<number>-<slug>.md` for ADRs.
- Use ISO dates (`YYYY-MM-DD`) in report filenames.
- Keep filenames stable after other documents link to them.

## Choosing the right document

| If you need to... | Create or update... |
| --- | --- |
| Plan a new feature | PRD under `requirements/backlog/` |
| Fix a tracked bug or incident | IRD under `issues/backlog/` |
| Record why an architecture choice was made | ADR under `knowledge/private/architecture/` |
| Explain how the system works now | Knowledge document |
| Capture temporary personal thoughts | Human note under `notes/` |
| Record independent proof for one plan | That PRD or IRD's `qa/` folder |
| Record a repository-wide audit | `requirements/reports/` |
| Save a PRD map, wave plan or handoff packet | `requirements/plans/` |
| Record a project-wide standard such as the Definition of Done | `knowledge/private/standards/` |

## Lifecycle gate

Folder location is the lifecycle status:

```text
backlog -> in-work -> completed
```

Do not copy a folder to the next state and leave the original behind. Move the entire folder. Do not mark work complete because code exists; move it only after its acceptance criteria are verified and required security and quality checks pass.

## Maintenance and verification

1. Library owns scaffold READMEs, this standard, and PRD/IRD lifecycle rules. Narrative and wiki authors own their pages; contract authors own CTR terms; QA reviewers own QA findings. Root README navigation is maintained separately.
2. Before editing, verify the repository root and branch and preserve other workers' changes. Ordinary documentation-only work does not introduce a feature implementation or authorize a commit, push, installation, or external service.
3. Check required v2 folders, README description fields, relative links, source citations, and whitespace. Report forthcoming pages or missing references explicitly. These are documentation checks, not runtime tests or proof of research execution.
4. No repository-specific contribution or security policy file was found in the tracked source inventory at initialization. Do not invent links, reviewers, or a release pipeline; obtain owner direction when needed.
5. Create the first PRD or IRD only for real work. IRDs require an existing GitHub issue, and PRDs must cite intended source files. Move whole folders with their QA history and repair relative links.
6. Do not create legacy v1 paths: `library/knowledge-base/`, `library/architecture/`, `library/requirements/features/`, `library/requirements/issues/`, or `library/qa/`. Flag any existing legacy artifacts instead of silently migrating them.
7. Use ordinary hyphens in newly authored prose. Keep source observations, proposed changes, and checks not run clearly distinct.

Reserved empty domains and lifecycle directories are intentional; Git does not preserve empty directories. The human-only `notes/` directory has no agent-authored content or README seed because the agent's no-write rule applies there.

## Reusable templates and evidence

Adapt the existing repository template to the reader's outcome. Identify the real workflow, template origin and source revision before generalizing. Keep current behavior, proposed requirements and unrun checks distinct. A commit URL identifies committed content; dirty working-copy sources also need their byte hash. Preserve project assumptions, failure ordering, accepted contract pins and approval boundaries. Assign a maintenance owner and review when the source changes. A copied checklist is not proof that the workflow ran. Keep customer records and secrets out of reusable templates.
