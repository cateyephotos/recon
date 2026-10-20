# Contributing to Recon

Recon's implementation is [skills/recon/SKILL.md](skills/recon/SKILL.md). It is an instruction-driven agent skill, not a shell program or application package.

## Setup

Clone the repository and follow the [README installation instructions](README.md#installation) to install the skill in a compatible host. There is no package installation, runtime environment file, build step, or development server in this repository. Research invocations use the host's tools and may incur model usage costs.

## Changes and review

Prepare focused pull requests against `main`. Use a separate branch for a proposed change; substantial feature work should use an isolated `feature/<slug>` worktree. Existing local feature-workflow instructions still apply where installed.

Use concise imperative commit subjects, following the existing history, such as `Fix report archive guidance`. No commit-message hook or release automation is installed.

Changes to the skill can affect contracts across distant sections. Check invocation defaults, targetless phases, compliance profile bundles, mandatory Markdown output, archive-before-research ordering, and comparison reports together when relevant. Explicitly document intentional behavior changes instead of silently resolving existing ambiguities.

Curated documentation lives in the [Library](library/README.md). Update source documents rather than a derived wiki export. Never include private research output in a contribution: `recon-reports/` is ignored in this checkout.

## Local verification

Before requesting review, inspect the diff and check whitespace in both unstaged and staged changes:

```bash
git diff --check
git diff --cached --check
```

Resolve changed relative links and compare affected examples with the skill implementation. For behavior changes, follow the [manual smoke test](README.md#testing) in a scratch project with an authorized public research target. Report the host used, what was checked, and any checks not run. A text check does not prove host execution.

There is no automated lint, typecheck, or test suite. CI is intentionally deferred because of billing problems; do not wait for nonexistent checks or enable automation without the owner's approval. See the [automation status](.github/AUTOMATION.md).

## Pull requests and issues

Use the [pull request template](.github/PULL_REQUEST_TEMPLATE.md) and [issue templates](.github/ISSUE_TEMPLATE/). Record evidence and compatibility effects. Update [CHANGELOG.md](CHANGELOG.md) for notable changes, not as a mandatory entry for every edit.

[CODEOWNERS](.github/CODEOWNERS) identifies the repository owner for review. Required approvals depend on GitHub branch rules; the file alone does not enforce a merge gate.

Do not post sensitive vulnerability details in public issues, pull requests, or discussions. A monitored private reporting channel and `SECURITY.md` are deferred by the owner; GitHub private vulnerability reporting is currently disabled.

## Releases

There is no automated release or deployment process. Changes are distributed by copying the skill as described in the README. Keep new changelog entries under `Unreleased` until a maintainer explicitly approves a release. Do not invent release tags, dates, or version support promises.
