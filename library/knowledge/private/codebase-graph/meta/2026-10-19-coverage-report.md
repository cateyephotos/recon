---
type: meta
title: "Recon partial filename coverage"
status: seed
created: "2026-10-19"
updated: "2026-10-19"
tags:
  - meta
  - codebase-graph
related: []
sources:
  - "README.md:1"
  - "skills/recon/SKILL.md:1-9"
partial_scan: true
source_revision: "0c5005462d63099de6d04d977207fcce3a03f22e"
---

# Recon partial filename coverage

## Scope and evidence

Confirmed direct-invocation scope: `README.md:1` and `skills/recon/SKILL.md:1-9` only. This is filename coverage, not semantic documentation or a code-graph refresh.

- `entities/README.md` records the source `README.md`.
- `entities/SKILL.md` records the source `skills/recon/SKILL.md`.
- Both are unsupported Markdown stubs. `module` is the stub schema default, not an extracted runtime module.
- Two files yield two stubs; the usual 8-15-page target does not justify invented entities.

## Source snapshot

Read-only git checks on 2026-10-19 verified branch `main` and HEAD `0c5005462d63099de6d04d977207fcce3a03f22e`. For both source paths, `git log -1 --format='%H %an %aI' -- <path>` returned commit `3deeab6cfbdd445f9fd50f5f8db3e699377ea2d3`, author AutomationGod, timestamp `2026-02-24T20:40:24-05:00`.

`git diff -- README.md` showed uncommitted installation edits (`README.md:37-39`), testing instructions (`README.md:111-118`), and Library navigation (`README.md:198-206`). No staged changes were reported for either source; `git diff -- skills/recon/SKILL.md` was empty. Commit hashes alone do not identify the scanned README working copy.

SHA-256 of source bytes at scan time, measured with `shasum -a 256`:

- `README.md`: `ddb29b1a6288dec7deafd7e150689bf9fed77089519b6c4278c604e744fa2830`
- `skills/recon/SKILL.md`: `627382f20c6a4547da9a7d0a2989497830701226b6e7a32b536b8945e62cb5fd`

The README digest was refreshed after adding Library navigation. These digests identify the final source bytes inspected during this documentation update, not any later edits.

## Graph limitations

- No Markdown AST, symbol, call, import, dependency, or backlink graph was extracted. Empty relationship lists do not prove that relationships are absent.
- No prior graph pages existed at the owned output path when checked. Unsupported stubs do not perform semantic contract comparison; no contradiction findings is not a clean-contract verdict.
- `.hivemind` was absent in the filesystem check. The caller reports no driver, queue, or graph-refresh tool is available. No driver state was bootstrapped and no refresh was claimed.
- `partial_scan: true` is a disclosure, not a scheduled reconciliation. No global-state reconciliation occurred; no automatic later pass is promised.
- No global indexes, logs, hot cache, hash manifests, source files, architecture narratives, ADRs, or PRDs were authored by this invocation.
- Existing edits were left in place. Runtime tests, external research, installs, and host-agent smoke tests were not run; the source's manual testing instructions are at `README.md:111-118`.
