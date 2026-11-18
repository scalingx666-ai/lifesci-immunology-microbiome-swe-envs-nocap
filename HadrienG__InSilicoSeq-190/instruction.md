# Issue

**Title:** InSilicoSeq compatibility with Biopython 1.78

## Description

Greetings,

Following update to Biopython 1.78, _iss/generators.py_ and a few tests fail to run due to deprecation and removal of _Bio.Alphabet_.  This was first reported in issue #189 .  Following instructions provided at https://biopython.org/wiki/Alphabet, I came up with a patch that should address this issue.

I hope this helps,
Kind Regards,
Étienne.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4be3a63f058`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.