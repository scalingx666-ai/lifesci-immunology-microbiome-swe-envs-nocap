# Issue

**Title:** fix tmpdir being set from base command

## Description

Prior to this pull-request, `TMPDIR` was set using `tempfile.gettempdir()` at the time and using the current env of the Aviary command being run. However, when jobs are submitted to a HPC cluster, often they have a bespoke `TMPDIR` set for each job (e.g. to clean up tmp files after job is finished).

So, essentially, the PR is to allow jobs to fall back to their `TMPDIR` env variable if one was not forced by using `--tmpdir`.

- [ ] Integration tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf906684a806`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.