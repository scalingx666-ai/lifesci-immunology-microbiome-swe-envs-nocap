# Issue

**Title:** Give the three single-label QIIME2 processes enough memory to start

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] `CHANGELOG.md` is updated.

## Description

A test task should not need a retry to succeed.
Three QIIME2 processes did, every time.

QIIME2 needs about 1.2 GB just to start.
`QIIME2_EXPORT_RELTAX`, `QIIME2_FEATURETABLE_GROUP` and `QIIME2_INTREE` were labelled `process_single`, which gives 1 GB, so their first attempt was killed with exit 137 and the second one, at 2 GB, succeeded.
This shows up in CI logs and slows every run that uses them.

They now use `process_low` for memory (3 GB, like the other QIIME2 processes) and `process_cpu_single` to stay at one CPU, as `QIIME2_TRAIN` does.

Verified with `nf-test test tests/default.nf.test --profile +docker`: no task needed a retry, and both processes ran with 1 CPU and 3 GB, peaking at 1.1 and 1.2 GB.

Analysis and implementation done with Claude Code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `183a6c471c32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.