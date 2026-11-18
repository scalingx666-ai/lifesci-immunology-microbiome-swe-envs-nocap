# Issue

**Title:** fix: conda-related fixes

## Description

Two changes to address the Conda failures / snapshot mismatches seen in #1083.
1. **Update the Prokka module.** GNU parallel `20260422+` fails every local job when `SHELL` isn't exported (`exec failed:No such file or directory`), which makes Prokka exit 2. The current module version pins `parallel=20241122` (nf-core/modules#11754). Containers ship an older parallel, hence Conda-only.
2. **Explicitly disable NanoPlot static images** (empty `-f`) in `tests/nextflow.config`. NanoPlot defaults to `--format png`, rendered via Kaleido, which needs Chrome. The runners have it, so Conda runs emit PNGs and container runs don't, causing snapshot drift.

## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4963e40159d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.