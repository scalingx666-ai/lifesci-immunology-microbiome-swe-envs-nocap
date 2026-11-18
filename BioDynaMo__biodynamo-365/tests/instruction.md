# Issue

**Title:** [CMake] Replace wget with FetchContent in CMake scripts.

## Description

I've replaced the usage of wget with FetchContent in the CMake files. However, I haven't removed it from the dependencies because there are still bash scripts that depend on it.

This helps reduce the dependency on wget at CMake configure time which is non-standard for OSX.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96ca70f99637`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.