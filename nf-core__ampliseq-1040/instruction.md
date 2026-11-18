# Issue

**Title:** Try GitHub-hosted ubuntu-latest runners for nf-test

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Description

The self-hosted `runs-on=...` runners used by `nf-test.yml` are stuck queued (see e.g. PR #1038, queued since 2026-07-31 with no runner ever picking it up). Switching all three jobs (`nf-test-changes`, `nf-test`, `confirm-pass`) to GitHub-hosted `ubuntu-latest` runners, same fix already applied to nf-core/magmap and nf-core/metatdenovo for the same symptom.

This drops the `4cpu-linux-x64`/`2cpu-linux-x64` sizing and the 80GB volume previously reserved for `test_multiregion` with singularity — worth watching whether that profile still fits on the standard `ubuntu-latest` disk allowance; if not, we may need a narrower fix (e.g. only exempting that one matrix cell).

No CHANGELOG entry — this is CI-only, not a user-facing pipeline change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45301559dde9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.