# Issue

**Title:** Remove only netsim's own checkpoint files after a run

## Description

.

After a successful checkpointed run, `netsim_clear_checkpoint()` unlinked the whole `.checkpoint.dir`, so pointing it at an existing project or output directory deleted everything in it. It now removes the per-simulation checkpoint files (and any leftover `_tmp` files), then the directory only if it is empty. The `.checkpoint.keep` docs in `?control.net` now say what is removed.

The new test in `test-netsim.R` runs a checkpointed model into a directory that already holds a file and checks the file is still there afterward. It fails on main.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8d8addcf5c09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.