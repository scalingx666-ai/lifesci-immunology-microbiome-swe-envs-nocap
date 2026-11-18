# Issue

**Title:** Patch release v1.0.1

## Description

## v1.0.1 - [2023-02-27]

### `Added`

-  Added pipeline DOI to `WorkflowMain.groovy` to display citation info when executing the pipeline. (by @jasmezz)

### `Fixed`

-  Removed a header check in the `check_samplesheet.py` script that was producing false negatives. Presence of required columns is still validated. (by @Midnighter)
-  Improved database downloading guidance to emphasise it is recommended to let nf-core/funcscan do the downloading on a first run, rather than manually downloading yourself. (reported by @alexhbnr, fixed by @jfy133)

### `Dependencies`

### `Deprecated`

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ba8ce333826`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.