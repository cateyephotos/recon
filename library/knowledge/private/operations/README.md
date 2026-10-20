---
ai_description: |
  Source-backed guidance for invoking Recon through a host agent and handling
  its reports. Do not invent shell commands, services, or deployment steps.
  Narrative authors maintain the usage guide independently of this scaffold.
human_description: |
  How to use the Recon skill and locate its research outputs.
---

# Operations

Read [Recon usage](recon-usage.md). The source is [`skills/recon/SKILL.md`](../../../../skills/recon/SKILL.md); `/recon` is a host-agent command, not a shell executable. Reports belong in `recon-reports/` in the invoking project. This scaffold does not run the skill.
