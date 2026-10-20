# Recon Usage

> Category: Operations | Version: 1.0 | Date: October 2026 | Status: Active

For operators and contributors, this guide explains host installation, scoped invocation and manual verification without implying a Recon application runtime.

**Related:**
- [Recon workflow](../architecture/recon-workflow.md)
- [Repository README](../../../../README.md)
- [Recon instruction implementation](../../../../skills/recon/SKILL.md)

---

## Why this exists

Use Recon through the host's `/recon` slash command, not a shell program named `recon`. The host interprets `skills/recon/SKILL.md` and supplies the research tools and model execution. This repository has no runtime, build step, automated test suite or deployment pipeline; inspecting or copying the instruction file does not prove a successful research run (`skills/recon/SKILL.md:1-16`; `README.md:111-118`).

## Install into the host

The README documents Claude Code installation by copying the skill folder and restarting the host. Claude Code must already be installed/configured, with WebSearch and WebFetch available; Reddit MCP is optional (`README.md:29-52`, `192-196`). The commands below document that workflow only. This documentation task did not execute them, and a GG projection does not itself establish native Claude Code installation or tool availability.

For a fresh global installation, run these shell commands from the directory that should contain the cloned checkout:

```bash
git clone https://github.com/g-baskin/recon.git
mkdir -p ~/.claude/skills
cp -r recon/skills/recon ~/.claude/skills/recon
```

The `mkdir -p` step creates the destination parent before copying. For an existing checkout, use its actual `skills/recon` path instead of cloning again. Inspect an existing destination before copying; the README gives an installation recipe, not a defined upgrade or duplicate-copy procedure (`README.md:33-42`).

For a project-only installation, run this alternative from the intended project's root, replacing the source path:

```bash
mkdir -p .claude/skills
cp -r /path/to/recon/skills/recon .claude/skills/recon
```

Restart Claude Code after installation. The global recipe makes the command available across projects; the project-level recipe scopes the copied skill to one project (`README.md:42-52`). These are installation instructions for a user-authorized operation, not automatic hooks or provider setup.

## Choose explicit scope in the invoking project

Open the project that should receive the reports before invoking the host command. Research phases 1-2 take external targets, while targetless `--phases 3,4,5` assesses your own build. Phase 5 explicitly concerns "OUR build" (`skills/recon/SKILL.md:1237`, `1291-1305`).

These examples are host inputs, not Bash commands; replace the sample research URL with an authorized target:

```text
/recon --quick https://example.com
/recon --phases 1,2 https://example.com
/recon --phases 3,4,5
/recon --phases 3 --compliance hipaa
/recon --phases 3 --compliance gdpr,hipaa,pci
/recon --phases 3 --compliance government
/recon --phases 1,2 --format json https://example.com
/recon --phases 1,2 --diff https://example.com
```

Quick mode limits Phase 1 to a product overview, pricing summary, three competitors and basic stack. Phase 3 runs the Shared Foundation before selected modules, defaulting to GDPR/SOC 2/OWASP. `hipaa` already includes HITRUST; `fedramp` includes NIST 800-53; `nist` means NIST CSF. Do not add `nist` merely to restate the government bundle's existing NIST 800-53 coverage (`skills/recon/SKILL.md:66-104`, `369-374`, `432-470`).

The current [Invocation Scope](../../../../skills/recon/SKILL.md#invocation-scope) table distinguishes the defaults: `/recon` without scope flags runs all five phases; natural-language requests without scope flags run phases 1-2. Explicit scope flags retain their documented meanings. Conflicting flags and invalid profiles still have no defined parser/error contract; this clarification does not establish one.

## Inspect outputs and protect the baseline

Expect files under `recon-reports/` in the invoking project, followed by a chat summary pointing to the saved report. Markdown remains mandatory even with JSON or CSV exports. For multiple targets, inspect individual reports before the cross-target `COMPARISON_MATRIX.md` (`skills/recon/SKILL.md:126-171`, `197-216`).

Before a rerun, inspect the existing target report and dated history. A current `RECON_REPORT.md` triggers diff behavior even without `--diff`: the host should move it into `previous/RECON_REPORT_[date].md` before new research, then produce the new report and `DIFF_REPORT.md`. Same-day collisions and missing-baseline diff behavior are unspecified; resolve those conditions before relying on the rerun to preserve research. No automatic recovery is documented (`skills/recon/SKILL.md:238-248`).

Read report content as well as metadata when checking scope. The metadata example records depth, phases, format, diff, completion and previous runs, but not compliance selection. The source also does not name the report folder for targetless builds. Neither gap justifies claiming equivalent scope or inventing a canonical folder rule (`skills/recon/SKILL.md:132-163`, `1296-1299`).

## Manual smoke test and contributor checks

The approved README smoke test uses a scratch project to avoid affecting existing research. After an authorized installation and restart, run `/recon --quick <target-url>` inside Claude Code against a public site you are authorized to research. This consumes host web tools and model usage; it is not a local automated test (`README.md:113-118`).

Check that the scratch project contains `recon-reports/[target-name]/RECON_REPORT.md` and `metadata.json`, that the report covers the four quick-mode topics, that metadata records quick depth and Phase 1 only, and that the chat summary points to the report. An unrecognized command indicates host discovery or installation trouble; missing web tools prevent a complete research smoke test (`README.md:115-118`).

For instruction or documentation changes, compare the flags, invocation examples, profile/bundle definitions, output rules and diff rules together. Check local Markdown links and whitespace separately from host behavior. Phase 4's requested verification passes are report instructions for a user's build, not an automated test suite or enforceable launch gate in this repository (`skills/recon/SKILL.md:1210-1231`).

This documentation pass inspected local sources and checked the two narrative files only. It did not install Recon, invoke `/recon`, contact external services, generate reports or verify host behavior. The [workflow source ledger](../architecture/recon-workflow.md#source-and-edge-ledger) pins the inspected bytes and records diagram limitations. No ADRs or PRDs underpin additional operational guarantees.
