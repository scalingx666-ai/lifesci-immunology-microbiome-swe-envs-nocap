# Issue

**Title:** DOC: fix inconsistency in tree center button documentation

## Description

The behavior of this button was changed during comments in #212, but the corresponding help text wasn't updated. This fixes that.

(sorry -- I was going to comment this in #212 this morning, and then that PR got merged in :sweat_smile:)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `39a342de88b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.