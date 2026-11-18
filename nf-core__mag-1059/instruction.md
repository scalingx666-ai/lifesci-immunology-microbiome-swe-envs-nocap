# Issue

**Title:** feat: make chopper default for longread qc

## Description

- Makes `chopper` the default long read filtering tool instead of `filtlong`. Chopper does the same job with less overhead; `filtlong` and `nanoq` stay available via `--longread_filtering_tool`.

- Adds `--longread_filtering_by_shortreads` (default: `false`). Before this, filtlong always tried to join short and long reads to derive quality from k-mer matches, which could drop long reads that didn't overlap the short read set. Now that behavior is opt-in.

- `test_hybrid` pins `--longread_filtering_tool filtlong` explicitly since the default changed.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d59e1b96dbc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.