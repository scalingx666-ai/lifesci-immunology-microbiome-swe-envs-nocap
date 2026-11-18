# Issue

**Title:** Basic language server-syntax fixes

## Description

This PR is the first one in a series to clean up our syntax to make it Nextflow language-server compliant.

It contains:

- Using of workflow input channels rather than params (when exsiting)
- Defining 'unique' variable names within operators rather than duplicating the same name as input channels
- Using the 'unused variable' syntax for variables within operators (i.e. `_FOO`)
- Ensuring local scope variables are defined correctly (and  in a way the language server is satisfied) 
- Reduced a couple of places of essentially duplicated code

I envision three more follow up PRs:

- Updating the currently syntax-problematic DIAMOND module
- Fixing the input validation code and location of inputs to the main `taxprofiler.nf` workflow
- Auto-formatting every file (once the previous PR is done)

## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/taxprofiler/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/taxprofiler _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec6a749e2a4d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.