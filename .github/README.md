# Repository automation status

CI is intentionally deferred at the owner's request because of billing problems. No workflow files are installed, including manual or scheduled workflows. Do not add or enable CI, CodeQL, release automation, or paid services until the owner explicitly approves resuming automation.

This setup does not change GitHub Settings. On 19 October 2026, GitHub reported zero repository Actions workflows. The absence of workflow files is not a repository-wide Actions disable switch.

Recon is a Markdown agent skill, not a Node or Python application. It has no dependency manifest, automated test suite, build, or deployment. Dependency update automation is not configured because there are no packages or Actions to update.

Use the local review and manual smoke-test guidance in [CONTRIBUTING.md](../CONTRIBUTING.md). See [CODEOWNERS](CODEOWNERS), the [pull request template](PULL_REQUEST_TEMPLATE.md), and [issue templates](ISSUE_TEMPLATE/) for contribution support.

## Before enabling automation later

1. Resolve billing and obtain the owner's approval.
2. Select checks that actually exist for this Markdown skill. Do not copy Node lint, typecheck, or test jobs without corresponding tooling.
3. Review workflow permissions and pin any adopted third-party Actions to verified full commit SHAs.
4. Only require a status check in branch rules after that check exists and can run. Requiring absent or disabled checks can block merges indefinitely.
5. Review dependency update automation only when packages or Actions have been introduced.

Private vulnerability reporting is currently disabled on GitHub. The owner deferred `SECURITY.md` until a monitored private contact is available; do not direct reports to an inactive reporting form or publish sensitive vulnerability details in issues.
