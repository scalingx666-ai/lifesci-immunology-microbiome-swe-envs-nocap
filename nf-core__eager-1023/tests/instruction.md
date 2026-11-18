# Issue

**Title:** Dsl2 add sharding of fastqs before alignment

## Description

<!--
# nf-core/eager pull request

Many thanks for contributing to nf-core/eager!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/eager/tree/master/.github/CONTRIBUTING.md)
-->
<!-- markdownlint-disable ul-indent -->

## PR checklist
Added functionality to shard fastqs before aligning. This uses SeqKit. The sharded fastqs are merged together during the lane merge step. 
- [X] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
    - [X] If you've added a new tool - add to the software_versions process and a regex to `scrape_software_versions.py`
    - [X] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](<https://github.com/>nf-core/eager/tree/master/.github/CONTRIBUTING.md)
    - [X] If necessary, also make a PR on the nf-core/eager _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [X] Make sure your code lints (`nf-core lint .`).
- [X] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [X] Usage Documentation in `docs/usage.md` is updated.
- [X] Output Documentation in `docs/output.md` is updated.
- [X] `CHANGELOG.md` is updated.
- [X] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6cb0c30762b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.