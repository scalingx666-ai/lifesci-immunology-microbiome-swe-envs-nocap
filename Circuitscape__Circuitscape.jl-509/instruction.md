# Issue

**Title:** CI: do not save the Julia depot cache from failed jobs

## Description

Root cause of the repeated Windows failure on #508, which was not a code problem.

`julia-actions/cache` runs with `save-always: true` by default, and caches are scoped per ref. #508's first Windows run failed partway through with LinearSolve resolved but its new dependency (`SparseColumnPivotedQR`) not yet installed; that depot was saved under `refs/pull/508/merge`. Every later run on the PR restored **its own broken depot** (`Cache restored from key: …run_id=33971116961;run_attempt=2` — the failed rerun), `julia-buildpkg` saw nothing to install, and precompilation of the project failed identically three times. Master, with its own cache, stayed green throughout.

Fix: `save-always: false` on every cache step, so only successful jobs persist a depot. The poisoned caches on #508's ref were deleted by hand to unblock it.

Part of the unreleased 6.0 (CI only).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6be7e32eb10e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.