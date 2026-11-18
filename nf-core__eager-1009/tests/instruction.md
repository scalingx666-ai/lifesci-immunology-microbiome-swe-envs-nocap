# Issue

**Title:** Dsl2 meta mapping function

## Description

Added `addNewMetaFromAttributes`, a function that can be applied with `.map` to create/replace a meta with renamed attributes. Then added using that instead of the repetitive channel operations we were doing before.

This does not seem to break `-resume` at all. For each instance of replacing the old channel operations, I reran the pipeline with `-resume` with parameters that would use the new implementation. All jobs were cached without issue.

I might have missed some use cases of the old channel operations somewhere. I should have gotten all the local subworkflows at least.

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

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fff960ba1862`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.