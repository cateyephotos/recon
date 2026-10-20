<!-- gg:init:start -->
# Recon

Recon is an agent skill for competitive research, technical teardown, and build-hardening assessments that persist reports in the invoking project.

`skills/recon/SKILL.md` is the implementation: YAML frontmatter exposes `/recon`, and the Markdown body defines argument handling, research phases, compliance modules, and report contracts. This checkout is not a Python application despite inherited context; it has no runtime, dependency manifest, test suite, or build/deploy pipeline. `/recon` is a host-agent command, not a shell executable.

## Cross-section contracts and traps

- Research phases 1–2 examine external targets; `/recon --phases 3,4,5` supports targetless build hardening, and Phase 5 concerns the user's own build. Do not make an external URL mandatory for every invocation.
- Output belongs under `recon-reports/` in the invoking project, not necessarily this skill repository. JSON/CSV exports supplement `RECON_REPORT.md`, never replace it: Markdown is also the comparison baseline. Finish individual reports before the cross-target `COMPARISON_MATRIX.md`.
- An existing target report activates diff behavior even without `--diff`. Archive it under `previous/RECON_REPORT_[date].md` before new research, then produce `DIFF_REPORT.md`; otherwise reruns lose their baseline. Same-day archive collision handling is unspecified.
- Phase 3 runs the Shared Foundation before selected compliance modules. Framework labels are not independent profile IDs: `hipaa` includes HITRUST, `fedramp` includes NIST 800-53, while `nist` means NIST CSF. In particular, adding `nist` to the government bundle changes its scope rather than representing its existing NIST 800-53 coverage.
- The `metadata.json` example omits compliance selection despite configurable profiles. Metadata alone cannot establish equivalent compliance scope between runs.
- Invocation scope is internally inconsistent: the flags tables default to all five phases, but the natural-language example specifies phases 1–2. Explicit `--phases` avoids that ambiguity; do not silently normalize the two behaviors when changing invocation handling.
<!-- gg:init:end -->
