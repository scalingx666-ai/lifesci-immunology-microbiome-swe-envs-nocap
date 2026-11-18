# Issue

**Title:** gc bias option

## Description

This PR implement a native GC bias option, with a 10% chance of rejecting a read if it fails outside of 40% - 60% GC content

See Issue #19

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e5b507877f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.