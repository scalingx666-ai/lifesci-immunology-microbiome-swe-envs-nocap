# Issue

**Title:** Launch the AWS tests with seqeralabs/action-seqera-launch and the v2 syntax parser

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
- [x] `CHANGELOG.md` is updated.

## Description

`seqeralabs/action-tower-launch` is archived and has no input for the Nextflow syntax parser.
The AWS test workflows now use `seqeralabs/action-seqera-launch` v1.0.0 (pinned to its commit) with `syntax-parser: v2` and `wait: running`.
The new action writes no debug log, so the artifact upload is removed.
A summary step writes the Seqera Platform run URL to the job summary.

The same change is merged or open in nf-core/taxmarker, nf-core/magmap, nf-core/metatdenovo and nf-core/phyloplace.
The magmap `awstest.yml` was dispatched from a branch with the change and launched a run on Platform.
Not yet run here; the first manual `awstest` dispatch after merge is the check.

🤖 Generated with [Claude Code](https://claude.com/claude-code)
Claude-Session: https://claude.ai/code/session_01UvGYU6kuXJeVv9ffdSzdzH

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c1235ac4888b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.