# Issue

**Title:** make sure htslib is built for the same arch

## Description

1. Fixes a tricky case when compiling on AppleSilicon (arm64) for x86_64 (happens, e.g., when cmake is x86_64).

All libraries are built for x86_64, but htslib checks compile for arm64 and fail linking against zlib compiled for x86_64.
Now we explicitly pass the target architecture for htslib.

2. Also, now we always link against the static locally compiled htslib binary.

3. Also improvements in the CI:
* compile with more threads
* correctly set the platform (previously all were Apple Silicon)
* check x86_64 build on arm64

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e81760fc5760`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.