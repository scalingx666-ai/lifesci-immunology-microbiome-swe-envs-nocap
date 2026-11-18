# Issue

**Title:** Apply suggestions from v.2.10 code review

## Description

Apply suggestions from code review + update release date.

PR into dev because I cannot directly push the @mashehu's suggestions somehow.

**Edit:**
All Nextflow 24.04.02 checks are failing because I specified a more recent Nextflow version in `nextflow.config` than what the template (and thus `ci.yml`) is using. Question for reviewers:

Leave like this or change back?

- Leave as is: all Nextflow 24.04.2 tests will fail (because >24.10.2 is specified)
- Change back: all conda tests will fail (would require Nextflow >24.10.2)
- Update version in ci.yml to 24.10.2 (would then be different from the template, but fix CI tests)

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81120541ee11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.