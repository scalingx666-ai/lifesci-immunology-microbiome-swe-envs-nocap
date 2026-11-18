# Issue

**Title:** Make corpus bootstrap immutable and safe across processes

## Description

Indexed corpus resolution previously accepted a cached array after its manifest was removed or its contents were corrupted. Fetching a changed index also overwrote the path already returned to another caller.

Store each published pair under an immutable identity derived from its index hashes. Verify both files on cache hits and coordinate writers with a bounded, crash-releasing process lock. Complete read-only caches avoid writer locks, and verified legacy files migrate without network access. Explicit local paths keep their existing precedence.

Validation: 63 signature/bootstrap tests passed, including independent-process download deduplication, partial/corrupt repair, version isolation, active-owner timeout, killed-writer recovery, offline legacy migration, and partial-file cleanup. Lint passed. Filesystem guarantees are locally tested; shared cluster filesystem behavior remains unverified.

This is a shared bootstrap dependency for the mirpy release audit. No fitted models, scientific thresholds, or corpus parameters changed. Release and downstream dependency updates follow CI and normal publication gates.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3061f5b6d79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.