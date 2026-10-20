---
status: accepted
date: 2026-02-24
recorded: 2026-10-19
---

# ADR-001: Adopt GPL-3.0 instead of MIT

## Context and Problem Statement

Recon originally used the MIT license. On 24 February 2026, commit [`9230782`](https://github.com/g-baskin/recon/commit/9230782957374f948ff96ac61f9f1485f6fbeabb) replaced it with GPL-3.0 and updated the README and skill license declaration.

The commit states the rationale: "Ensures modifications must be shared back and credit is preserved." This record captures that already implemented choice retrospectively. It does not represent a new licensing decision or an approval of additional terms.

## Considered Options

The available history establishes the former license and its replacement, not a formal options review:

- Retain MIT, the license present in the parent of `9230782`. It permitted modification, distribution and sublicensing subject to preserving its copyright and permission notices.
- Adopt GPL-3.0, the choice implemented in `9230782` to support the recorded sharing and credit goals.

No evidence of other evaluated licenses, a review panel, or a detailed rejection analysis was found. Those details are not inferred.

## Decision Outcome

The project adopted GPL-3.0, replacing MIT in that revision. The recorded motivation was preservation of credit and sharing of modifications. The authoritative terms are the repository's [LICENSE](../../../../LICENSE), not the shorthand wording in the commit or this ADR.

This decision is consequential because it changes the permissions and conditions communicated to recipients of distributed versions. It is not a label that can be renamed independently of the license and distribution history.

## Consequences

- **Intended benefit:** the sharing and attribution goals are recorded alongside the chosen license, so future maintainers need not reconstruct the reason from Git history.
- **Distribution tradeoff:** GPL-3.0 contains notice and licensing conditions for conveying source and modified source versions (sections 4 and 5). Distributors must assess those conditions rather than assume the prior MIT terms apply to the current revision.
- **Scope limit:** section 2 separately addresses works that are not conveyed. The commit's phrase "shared back" must not be read as an extra obligation to submit every private modification to the original author.
- **Documentation consequence:** future changes to this decision should be recorded in a superseding ADR, not by silently rewriting this accepted historical record. This ADR does not change LICENSE or claim to resolve the status of previously distributed copies.

## Evidence

- The decision and stated motivation: commit `9230782957374f948ff96ac61f9f1485f6fbeabb`, "Switch license from MIT to GPL-3.0".
- The former terms: `LICENSE` in that commit's parent, inspectable with `git show 9230782^:LICENSE`.
- The implemented terms: [LICENSE](../../../../LICENSE), particularly sections 2, 4 and 5.
- The current declaration: [README license section](../../../../README.md#license) and [skill author/license header](../../../../skills/recon/SKILL.md).

This is a source-backed decision record, not legal advice or a new license grant.
