# Issue

**Title:** Use MoreUtils for backwards compatability

## Description

Older List::Util modules don't have "all". Simply specifying MoreUtils will solve this (as is used in the downloadRefSeq.pl script, so there's no extra lib to download).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `881373c9023b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.