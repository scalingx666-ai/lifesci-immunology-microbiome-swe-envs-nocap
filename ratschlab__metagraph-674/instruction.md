# Issue

**Title:** Small sanitizer and stream-validation fixes

## Description

Fix four sanitizer and stream-validation issues independently of the alignment refactor in #672.

- Avoid using the logger during process-exit temporary-directory cleanup, when it may already be destroyed.
- Reject failed RowSparse input streams before decoding vectors.
- Keep bit-vector serialization fixtures alive through their checks; the previous `initializer_list` storage could dangle.
- Link Folly's `SanitizeLeak.cpp` in sanitizer builds so leak annotations resolve.

[CI on this branch](https://github.com/ratschlab/metagraph/actions/runs/39825321666) passed 49 jobs, with two expected skips, including the Docker build. A stalled Ubuntu package-install job was retried on the same commit.

Developed and tested with Codex and Claude Code assistance; human review is required.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ceb83b2ab077`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.