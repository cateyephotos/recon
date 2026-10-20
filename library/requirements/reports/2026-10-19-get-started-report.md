# Recon Get Started verification

Date: 19 October 2026. Scope: the applicable repository baseline from `get-started-stinger`, adapted to a Markdown agent skill. This is not an application security audit or a completed Ship Gate.

The owner requested that CI remain inactive because of billing problems, then explicitly deferred the security policy until a monitored private contact is available. No GitHub Settings were changed. No packages, hooks, native-client integrations, or home instructions were installed. Nothing was committed or pushed.

## 1. Already present

Existing files were preserved, including changes from earlier tasks. SHA-256 checks confirmed that all 32 pre-existing files in the inspected root, skill, and Library set were unchanged before recording the separate CI checklist result.

These template targets differ from the Get Started template and were not touched:

| File | Existing customization preserved |
| --- | --- |
| `README.md` | Actual installation, manual testing, profiles, and Library links instead of a generic application scaffold |
| `library/README.md` | Recon-specific purpose, source links, and wiki coverage limits |
| `library/knowledge/README.md` | Repository-relative audience navigation |
| `library/knowledge/public/README.md` | Local public-domain paths rather than template machine paths |
| `library/knowledge/private/README.md` | Recon architecture, operations, and graph navigation |
| `library/knowledge/private/contracts/README.md` | Local contract wording and no sample accepted contracts |
| `library/knowledge/private/standards/documentation-framework.md` | Recon-specific schema and source-versus-derived documentation rules |
| `library/requirements/README.md` | Local lifecycle paths and no invented approved plans |
| `library/requirements/backlog/README.md` | Recon-specific wording for planned PRDs |
| `library/requirements/completed/README.md` | Skill-appropriate completion wording rather than application production claims |
| `library/requirements/reports/README.md` | Local routine-report guidance |
| `library/issues/README.md` | Repository-relative issue lifecycle paths |

These template targets already match and were unchanged:

- `library/requirements/in-work/README.md`
- `library/issues/backlog/README.md`
- `library/issues/in-work/README.md`
- `library/issues/completed/README.md`

Other existing files, including `LICENSE`, `STATUS.md`, `CLAUDE.md`, `skills/recon/SKILL.md`, the narrative knowledge docs, and partial wiki pages, were preserved. GPL-3.0 is already selected; no license decision was made here. Earlier source-grounded Knowledge documentation remains applicable because the skill and README were not changed in this run.

## 2. Created this run

| File | Adaptation and evidence |
| --- | --- |
| `.gitignore` | Retained environment-file protections and the example exception; omitted irrelevant Node caches; ignored local `recon-reports/` and OS/editor temporary files |
| `.editorconfig` | UTF-8, LF, final newlines, two-space indentation, and preservation of Markdown trailing spaces; no formatter installed |
| `.github/CODEOWNERS` | `@g-baskin` resolved from the remote and GitHub repository-owner metadata; explicitly covers `.github/` and ownership changes |
| `.github/README.md` | Records the CI billing hold, absence of workflows, local verification, and conditions for later activation |
| `.github/PULL_REQUEST_TEMPLATE.md` | Requests real local/manual evidence without nonexistent lint/typecheck/test commands |
| `.github/ISSUE_TEMPLATE/bug_report.md` | Host, skill revision, invocation, and sanitized reproduction information; no application runtime invented |
| `.github/ISSUE_TEMPLATE/feature_request.md` | Research task, proposed behavior, and observable acceptance outcome |
| `CONTRIBUTING.md` | Existing `main` branch and imperative commit style, manual skill verification, no release automation or false private reporting route |
| `CHANGELOG.md` | Only observed, unreleased changes; no invented version, release date, or tag |
| `library/requirements/plans/README.md` | Missing schema-v2 planning folder, without pretending any build plan is approved |
| `library/requirements/reports/2026-10-19-get-started-report.md` | This inventory, evidence, and deferred decisions |

All template configuration placeholders were replaced or omitted where not applicable. Issue and PR prompts are intentionally fillable contributor fields, not unresolved setup values.

### Local verification

A read-only Python check using the already installed YAML parser passed for the ten baseline files preceding this report. It checked 15 local links and anchors, issue/Library YAML frontmatter, EditorConfig parsing, shell-snippet syntax, CODEOWNERS syntax, Markdown fences, whitespace, and absence of template machine paths or unresolved configuration tokens.

Thirteen `git check-ignore` cases passed: environment variants, research output, and temporary files are ignored; `.env.example`, skill sources, docs, ownership, and future local command files remain trackable. All 32 pre-existing file digests matched the pre-write inventory. No workflow YAML, security policy, or completion lock was created.

There is no project test suite, lint command, typecheck, or build to run. Live skill execution, installation, Mermaid rendering, secret scanning, GitHub interpretation of the unpushed CODEOWNERS file, and remote link availability were not tested.

### GitHub observations

Read-only `gh api` calls confirmed:

- Repository: `g-baskin/recon`, public, default branch `main`, owner `g-baskin`.
- `repos/g-baskin/recon/actions/workflows`: `total_count` is `0`.
- `repos/g-baskin/recon/private-vulnerability-reporting`: `enabled` is `false`.
- `repos/g-baskin/recon/community/profile`: published health score is `42%`, with README and GPL-3.0 present and contributor/issue/PR templates absent remotely.

The remote score is a pre-publication observation, not a score for this working tree. These local files cannot improve the remote profile until an approved commit and push lands them on the default branch.

## 3. Needs a human decision

### Explicitly deferred by the owner

- CI: leave all workflow creation and activation deferred for billing. This includes manual and scheduled workflows, release jobs, and CodeQL setup. No workflow is installed; this is not a claim that the repository-wide Actions setting was disabled.
- Security policy: no `SECURITY.md` until the owner supplies a monitored private contact or enables and verifies GitHub private reporting. Do not publish a disabled reporting link, fake email address, response-time guarantee, or unsupported version policy.

### Settings and governance not changed

- Review branch rules for PR requirements, Code Owner approvals, and blocked force pushes. Do not require absent or disabled CI checks. Existing branch rules were not audited.
- Review secret-scanning and push-protection availability and settings without enabling paid services automatically. Existing scanning settings were not audited.
- Choose a code of conduct and its enforcement contact if desired. `CODE_OF_CONDUCT.md` is not in this Stinger's templates and was not invented.
- Choose hook or commit-message enforcement only if the project wants it. Neither husky, lefthook, nor commitlint was installed; adding a Node toolchain solely for this Markdown repository is not assumed.

### Not applicable or intentionally omitted

- `.nvmrc`: no Node runtime or package manifest.
- `.env.example`: the skill reads no project-specific environment variables. Host credentials are configured outside this repository; no fake application settings were added.
- `.github/dependabot.yml` or Renovate: no package dependencies or Actions to update. Reassess only when these exist.
- `library/notes/README.md`: human-only notes were not read or written. The existing scratch directory was left alone.
- `wasp-nest.lock`: not written because setup is intentionally partial, with CI and security-policy work deferred. The lock must not imply a completed baseline.

Before committing these additions, run `security-stinger`, then `quality-stinger`, then `github-repo-health-stinger`, and present their reports for the owner's review and explicit commit/push approval. Those Ship Gate reviews were not run as part of this add-only setup.
