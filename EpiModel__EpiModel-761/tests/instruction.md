# Issue

**Title:** make tracker.net functionality the default behavior

## Description

- rename `tracker.net` to `epi_trackers`
- remove the need to pass `at` to the trackers. Most of the time it is
  not needed and if it is it can be accessed with `get_current_timestep`
- rename the control argument `tracker.list` to `.tracker.list` to
  insist on the "internal" aspect of it (similar to the updater arguments)
- modify the tests to match the new API
- modify the vignette to match the changes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `22270e560b37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.