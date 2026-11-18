# Issue

**Title:** Share ROOT package selection between downloads and cache checks

## Description

ROOT downloads and cache validation derive their checksum keys separately. For example, Xcode 16.4.1 selects the Xcode 16.4 ROOT package for download, but the cache check looks for a nonexistent 16.4.1 checksum. This causes CMake to delete and download an otherwise valid ROOT installation again.

Move the existing package mapping into shared helpers in `cmake/utils.cmake` and use the selected checksum key for both downloading and cache validation. Normalize Xcode versions and compare their components with `VERSION_GREATER_EQUAL`, so versions such as 16.10 are ordered correctly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `553f69cb6ddf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.