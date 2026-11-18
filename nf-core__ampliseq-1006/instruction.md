# Issue

**Title:** Update nf-schema from 2.5.1 to 2.7.2

## Description

`NXF_VER=26.04.1 nextflow run nf-core/ampliseq -r 2.17.0 --outdir results -profile singularity,test --skip_qiime`
leads to 
```
ERROR ~ Validation of pipeline parameters failed!
The following invalid input values have been detected:
* --skip_qiime (true): Value is [string] but should be [boolean]

```
Same is true for the current `dev` branch or with `NXF_VER=26.04.0`, but `NXF_VER=25.10.4` yields no error.

nf-schema is updated here from 2.5.1 to 2.7.2 to resolve the issue with `NXF_VER=26.*`.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `434b8db94e30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.