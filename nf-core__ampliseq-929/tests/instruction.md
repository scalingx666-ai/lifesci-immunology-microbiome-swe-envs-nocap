# Issue

**Title:** Gracefully handle missing MultiQC plots

## Description

Solves 

MultiQC occasionally fails due to a bug in a dependency. Previously the subsequent pipeline summary report failed, now the report is generated regardless.
Instead of the plot, a small message (not a large big warning) says that a plot is missing:
<img width="832" height="176" alt="image" src="https://github.com/user-attachments/assets/0b79bb7b-7796-4796-b1ea-61f12f039a83" />

Alternatively the warning in the report could be omitted. Possibly (dont know yet how) a warning could go into the console/log (but thats currently not the case!).

The CI tests would fail (missing output files that are expected), that makes sure that we do not miss that in case MultiQC also fails to produce plot in the CI tests.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5132c29bf9d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.