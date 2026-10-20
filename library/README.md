---
ai_description: |
  Documentation library, schema v2. Read the folder README before writing.
  knowledge/ holds reference and audience explanations; requirements/ holds
  PRDs; issues/ holds IRDs. notes/ is human-only: do not read, write, summarize,
  or cite its contents. Keep generated binary packet files outside library/.
  Shared CTR records live in knowledge/private/contracts/.
human_description: |
  Start here to find product plans, issue plans, and reference documents.
  Public knowledge is approved for external readers; private knowledge is
  for the team. Notes are unmaintained human scratch material.
---

# Recon Library

This library documents Recon, a Markdown host-agent skill defined in [`skills/recon/SKILL.md`](../skills/recon/SKILL.md), not an application. Schema version: **v2**. There is no application runtime, dependency manifest, test suite, or build/deploy pipeline in this checkout.

Read each folder's README before adding a document. The full schema is in [`knowledge/private/standards/documentation-framework.md`](knowledge/private/standards/documentation-framework.md).

## Find a document

| Folder | What goes here |
| --- | --- |
| [`knowledge/public/`](knowledge/public/README.md) | Approved product overviews, public briefs, user guides, and FAQs |
| [`knowledge/private/`](knowledge/private/README.md) | Internal engineering and business knowledge, ADRs, shared CTR contracts, and standards |
| [`requirements/`](requirements/README.md) | Product requirements documents (PRDs), grouped by backlog, in-work, and completed |
| [`issues/`](issues/README.md) | Issue requirements documents (IRDs), using the same lifecycle |
| `notes/` | Human-only scratch space; agents do not read or write here |

## Recon documentation

- [Workflow and architecture](knowledge/private/architecture/recon-workflow.md)
- [Invocation and usage](knowledge/private/operations/recon-usage.md)
- [Documentation standards and coverage limitations](knowledge/private/standards/documentation-framework.md)

Narrative pages are maintained separately from this scaffold. Wiki coverage is partial: source-backed Markdown explanations are not proof of tree-sitter symbol extraction or a complete dependency graph. The `codebase-graph/` subtree, if present, has a separate owner; initialization does not generate or validate it.

Recon run outputs belong in `recon-reports/` in the invoking project, as specified by the skill, not in this Library's repository QA folder. No research run is performed by initializing these docs.

## Source documents and generated files

Keep curated Markdown sources in the proper knowledge domain. Keep brand assets, rendered sites, Word files, PDFs, and other build outputs outside `library/`, at the agreed output location. Edit the source and regenerate outputs instead of editing a generated mirror. Authored wiki Markdown belongs under `knowledge/`; a wiki export is a generated mirror.

A public packet contains only approved reader documents, safe citations, and approved visuals. Keep source paths, quotes, hashes, gaps, and review records in its private `_internal` area. Exclude that area from public delivery. Folder placement alone does not authorize publication.
