# Issue

**Title:** Update container

## Description

PR updating `environment.yml` in order to build the new container and get the test passing for PR #81. I had to change some dependencies since `python3` seems to be needed now because of some other dependency (`markdown`?). When I did not specify the python version I got an error when running the tests.

Many thanks to contributing to nf-core/hlatyping!

Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs).

## PR checklist
 - [ ] This comment contains a description of changes (with reason)
 - [ ] If you've fixed a bug or added code that should be tested, add tests!
 - [ ] If necessary, also make a PR on the [nf-core/hlatyping branch on the nf-core/test-datasets repo]( )
 - [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
 - [ ] Make sure your code lints (`nf-core lint .`).
 - [ ] Documentation in `docs` is updated
 - [ ] `CHANGELOG.md` is updated
 - [ ] `README.md` is updated

**Learn more about contributing:** https://github.com/nf-core/hlatyping/tree/master/.github/CONTRIBUTING.md

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `923ec0278e81`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.