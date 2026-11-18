# Issue

**Title:** Check curation and add status badge to PR

## Description

Curation status badge in PR body reports passing or failing and links to the action that created it. Status depends on curatedMetagenomicDataCuration:::checkCuration().

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c1862ae36684`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.