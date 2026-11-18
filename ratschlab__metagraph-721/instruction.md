# Issue

**Title:** Preserve case in case-sensitive DNA reverse complements

## Description

Make case-sensitive DNA reverse complements preserve case: `ACG` becomes `CGT`, and `acg` becomes `cgt`. Correct both packed complement tables to agree with the existing string helper.

Uppercase and lowercase A/C/G/T retain masking information as distinct indexed symbols. Lowercase bases remain eligible for matching.

Rebuild existing case-sensitive canonical and primary graphs and their dependent annotations. Basic graphs retain their previous behavior.

Cover construction, annotation, queries, contig/unitig extraction and rebuilding exported sequences in the regular test suites.

Prepared with Codex.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a381fde8822f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.