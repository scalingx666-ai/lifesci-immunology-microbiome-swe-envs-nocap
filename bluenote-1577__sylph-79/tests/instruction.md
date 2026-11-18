# Issue

**Title:** Two-stage profiling: db-convert + profile --two-stage

## Description

Hi,

Here's the result of some messing around with AI I did. It seems to be a straight up win for profiling by CPU, RAM and database disk size compared to the main branch, particularly for simple communities, though it does make the CLI interface and codebase a bit more complex. It might be a good idea to update the version of the current genome database, rather than create a new `syl2db`, but I'll leave that decision to you.

Results are **identical** to single-stage profiling, while profiling is
**~7–27× faster** and uses **~6× less RAM** (a flat ~4.4 GB vs the whole ~26 GB
database), and the on-disk database is **~22% smaller**.

See below comment at  for an updated description of the PR.

Thanks,
ben

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf6ee068c028`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.