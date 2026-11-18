# Issue

**Title:** Don't rename the taxonomy results -- also remove failOnError on publish

## Description

The taxonomy file results carried the _split_ in the name. This was introduced in the SPLIT_PROTEINS code recently. I've changed back the names of the files, but in the modules.config / publishDir.

I've removed the failOnError: false -> this could lead to runs that generate no results because a configuration error for example. I'm not sure what was the rationale, but if Nextfow can't copy the outputs it should fail.

I've added the serena tool folder to the ignore dir.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95776661c4f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.