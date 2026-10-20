---
ai_description: |
  Internal engineering and business documentation. ADRs live in
  architecture/ADR-<n>-<kebab-slug>.md; shared CTRs live in
  contracts/CTR-<###>-<slug>.md; documentation standards live in
  standards/documentation-framework.md. Add only source-backed domains.
  Internal evidence and unresolved findings must not become public by default.
human_description: |
  Knowledge for engineering, founders, sales, service, account teams, and
  other internal readers. Includes architecture, business insights, decisions,
  operations, and approved internal explanatory manuscripts.
---

# Knowledge: Private

Internal reference for Recon's Markdown skill. Folder placement is an audience convention, not access control; files in a public checkout remain publicly visible.

## Shared folders

| Folder | Contents |
| --- | --- |
| [`architecture/`](architecture/README.md) | Source-backed workflow narratives and `ADR-<n>-<kebab-slug>.md` decision records |
| [`contracts/`](contracts/README.md) | `CTR-<###>-<slug>.md` shared API, event, data, permission, or state agreements |
| [`standards/`](standards/README.md) | [Documentation framework](standards/documentation-framework.md) and repository writing rules |
| [`operations/`](operations/README.md) | Host-agent invocation and report handling |

## Add domains as needed

Use domains such as `auth/`, `data/`, `security/`, `operations/`, `strategy/`, `personas/`, or `reporting/` when the sources support them. Add a README that explains the domain. Do not seed unrelated domains or assume a technology stack.

Keep unsupported claims and unresolved source ambiguities explicit. This scaffold does not establish an application stack, operating service, or automated wiki sync.

## Store the right material

Keep PRDs in `requirements/` and IRDs in `issues/`. Keep curated explanatory Markdown here when it is internal. Put approved external Markdown in `knowledge/public/`. Keep brand assets and generated Word/PDF files at an agreed location outside `library/`.
