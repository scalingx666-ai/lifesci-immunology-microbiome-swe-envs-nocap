# Issue

**Title:** [MRG] Switch to using picklists for storing matches, as opposed to saving a copy of the signatures.

## Description

This PR uses the prefetch results as a picklist for the original database(s), rather than saving all of the matches in a new file. This can be a big space savings!

.

@taylorreiter ready for review!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2b428d3829b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.