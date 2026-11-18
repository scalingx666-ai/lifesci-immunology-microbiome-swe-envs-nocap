# Issue

**Title:** pulling and updated vsearch/cluster module from nf-core

## Description

Fixing bug  

I have pulled the updated nf-core/modules vsearc/cluster module into the dev branch of ampliseq. 
This should fix an arguments too long error froma wildcard expansion.

## PR checklist

- [ yes] This comment contains a description of changes (with reason).
- [ n/a] If you've fixed a bug or added code that should be tested, add tests!
- [ n/a] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [ n/a] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ yes] Make sure your code lints (`nf-core pipelines lint`).
- [ yes] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ yes] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ n/a] Usage Documentation in `docs/usage.md` is updated.
- [ n/a] Output Documentation in `docs/output.md` is updated.
- [ yes] `CHANGELOG.md` is updated.
- [ n/a] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `30f03f3f0e33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.