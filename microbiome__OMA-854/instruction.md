# Issue

**Title:** Update biocbook workflows

## Description

Some actions use nodejs 20, which is deprecated. I also updated the versions of other workflows.

That's usually the work of [DependaBot](https://docs.github.com/en/code-security/tutorials/secure-your-dependencies/dependabot-quickstart-guide) or Renovate.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d02425a6a6fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.