# Issue

**Title:** Patch nf schema -  include integer & string as type for sample

## Description

<!--
# nf-core/viralrecon pull request

Many thanks for contributing to nf-core/viralrecon!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

Currently, nf-schema would throw a misleading error message if a sample name contained only digits: 

`-> Entry 2: Error for field 'sample' (303452): Sample name must be provided and cannot contain spaces`

The newer version of nf-schema `v2.2.1` throws both the validation error message as the set error message: 
`->Entry 2: Error for field 'sample' (303452): Value is [integer] but should be [string] (Sample name must be provided and cannot contain spaces)`

Which is more clear. Additionally added that both strings and integers can be allowed as a type. 

- [X] This comment contains a description of changes (with reason).
- [X] If you've fixed a bug or added code that should be tested, add tests!
- [X] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)- [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [X] Make sure your code lints (`nf-core lint`).
- [X] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [X] Usage Documentation in `docs/usage.md` is updated.
- [X] Output Documentation in `docs/output.md` is updated.
- [X] `CHANGELOG.md` is updated.
- [X] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27b2c6cecdef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.