# Issue

**Title:** Add --tmpdir argument

## Description

To set default directory for tempfile. Used ChangeTempAction (with example code) from GTDBTk/gtdbtk/biolib_lite/custom_help_formatter.py.

I needed to do this on my system because prodigal threw an error that it couldn't find a file in the /tmp directory. With these changes the issue was fixed. On our system it is recommended that we use another directory for a temporary directory, I suppose this is why.

I added the --tmpdir argument to all workflows because I wasn't sure for which ones it was relevant.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66bd8e53a054`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.