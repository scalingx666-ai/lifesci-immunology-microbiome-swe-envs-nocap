# Issue

**Title:** Add exit code 247 to MEGAHIT retry error strategy

## Description

## Description

MEGAHIT can exit with code `247` when it runs out of memory (alongside the already-handled `250`). Previously this exit code caused the task to `finish` instead of `retry`, so out-of-memory runs failed permanently rather than getting a fresh attempt with more memory.

This PR adds `247` to the MEGAHIT `errorStrategy` retry list in `conf/base.config`.

```diff
-        errorStrategy = { task.exitStatus in ((130..145) + [104, 175, 250]) ? 'retry' : 'finish' }
+        errorStrategy = { task.exitStatus in ((130..145) + [104, 175, 247, 250]) ? 'retry' : 'finish' }
```

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] `CHANGELOG.md` is updated.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfcb60d4dcc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.