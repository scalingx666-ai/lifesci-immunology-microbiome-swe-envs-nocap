# Issue

**Title:** Fix zstr compilation on Mac OS X

## Description

This PR fixes an issue with Mac regression tests at bioconda/biocona-recipes#7213 and will also enable Kaiju to be compiled on Mac OS X.

This PR is straight from PR mateidavid/zstr#7.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8730c6fc1d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.