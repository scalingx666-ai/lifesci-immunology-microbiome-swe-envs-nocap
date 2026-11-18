# Issue

**Title:** Big Bakta update

## Description

- Version bump to bakta 1.7.0
- Incl. the parameter `params.annotation_bakta_db_light` to be able to switch between the light (1.3 GB) and full (33.1 GB) version of the Bakta DB
- Switched off unnecessary Bakta annotation steps by default.

 
 

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff783fc6f285`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.