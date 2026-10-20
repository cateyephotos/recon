---
ai_description: |
  Reference and explanatory documentation, split by audience. Default new
  documents to private/. Use public/ only for content approved for external
  readers. Write into the relevant domain folder, not this root.
  ADRs live in private/architecture/; shared CTRs live in private/contracts/.
human_description: |
  Public knowledge explains the product to external readers. Private knowledge
  explains the system, decisions, business, and operations to the team.
  This area includes explanatory briefs as well as reference and help guides.
---

# Knowledge

Knowledge documents explain how the product works, why its decisions matter, and what a reader needs to understand.

| Folder | Readers | Typical content |
| --- | --- | --- |
| [`public/`](public/README.md) | Approved external audiences | Product overviews, public briefs, user guides, and FAQs |
| [`private/`](private/README.md) | Internal team and agents | Architecture, ADRs, shared contracts, business insights, standards, and operations |

## Choose the audience first

Use `public/` for facts and explanations approved for external readers. Use `private/` for internal engineering, business, source evidence, or unresolved findings. When unsure, start in `private/` and ask the owner what may be shared. Investor and customer documents can still be private; the reader's role does not decide disclosure.

Create only domains supported by real source material. A PRD describes what to build; a knowledge document explains the system and its decisions. Distinguish planned behavior from current behavior when that difference affects the reader.

## Recon coverage

The implementation source is [`skills/recon/SKILL.md`](../../skills/recon/SKILL.md). The current documentation scope is a partial wiki, not an extracted application symbol catalog. See the [documentation framework](private/standards/documentation-framework.md) for ownership and graph limitations. Keep generated binaries outside the Library and do not expose private evidence through public documents.
