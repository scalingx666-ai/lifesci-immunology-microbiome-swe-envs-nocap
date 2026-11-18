# Issue

**Title:** Small fix for bacterial collections

## Description

Newest bacterial collection has a small change, test out this on your current branch, it will fail:

getENSEMBL.Seq("Escherichia coli", path = tempdir())

With this fix it works

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e82db6541f41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.