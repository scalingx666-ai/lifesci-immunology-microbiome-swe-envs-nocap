# Issue

**Title:** docs: add missing PyPOLCA citations

## Description

PyPOLCA was added as an optional short-read polisher for long-read assemblies in #1048, but its citation was never added.

This PR adds PyPOLCA to the three places a tool citation belongs:

- **`README.md`** — pipeline tool list.
- **`CITATIONS.md`** — full reference (Bouras et al. 2024, doi: 10.1099/mgen.0.001254).
- **`subworkflows/local/utils_nfcore_mag_pipeline/main.nf`** — `toolCitationText()` and `toolBibliographyText()`, gated on `params.run_pypolca`, so the auto-generated methods description and bibliography include PyPOLCA when the tool is run.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [x] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes.
- [ ] Check for unexpected warnings in debug mode.
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `197b8ba62ecc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.