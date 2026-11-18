# Issue

**Title:** Feat/add hypo uniref

## Description

<!--
# ebi-metagenomics/mettannotator pull request

Many thanks for contributing to ebi-metagenomics/mettannotator!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/ebi-metagenomics/mettannotator/tree/master/.github/CONTRIBUTING.md)
-->

The aim of this PR is to include a new source of annotation for hypothetical proteins, the details of benchmarks that supports this decision are [included here](https://embl.atlassian.net/wiki/spaces/MI/pages/332136455/Benchmark+annotation+with+Prokka+and+Bakta).

## New Feature

Two diamond analysis are performed using uniref90 and uniref50 databases, the output contains the entire title of subject, which includes the description of proteins that can be used in post processing processes to re-annotate hypothetical proteins.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/ebi-metagenomics/mettannotator/tree/master/.github/CONTRIBUTING.md)
- [ ] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0281d7b45a99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.