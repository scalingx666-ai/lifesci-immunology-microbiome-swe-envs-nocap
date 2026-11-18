# Issue

**Title:** Add explicit mkl dependency for rust-bio-tools

## Description

For some reason, rust-bio-tools, now that we got it updated to include blis as a dependency (#289), now depends on mkl as well (or instead? I actually *don't* see libblis used by the rbt binary in the latest builds).  I described my confusion about that in bioconda/bioconda-recipes#27826 but for our purposes adding mkl to our environment file seems to get it working again. .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f45f1841adea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.