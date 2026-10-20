---
ai_description: |
  Holds whole-project build plans, such as a PRD map, ordered wave plan,
  and handoff packet. No Recon build plan is currently approved.
  PRDs belong in backlog/, in-work/, or completed/, not here.
human_description: |
  Plans that coordinate multiple features. Approval of a specific revision
  is required before a draft becomes an implementation plan.
---

# Requirements: Plans

Use this folder for whole-project plans that span more than one PRD. Recon currently has no approved build plan or application deployment pipeline; this folder does not imply otherwise.

Typical documents are `prd-map.md`, `wave-plan.md`, and `handoff-packet.md`. Create them only for real planned work. Individual PRDs belong in the [requirements lifecycle folders](../README.md), and project-wide standards belong in [private standards](../../knowledge/private/standards/README.md).
