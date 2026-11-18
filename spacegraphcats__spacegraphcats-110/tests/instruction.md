# Issue

**Title:** Add a more manageable "real read" data set for testing - the shewanella reads

## Description

It became clear this week that "real" read data sets seem to introduce interesting new features into the cDBG - podar causes many more problems with components and minhashes than acido or 15genome, neither of which use real reads.

This PR introduces a new data set which is a subset of the reads in podar, obtained by mapping the reads from podar against a specific genome sequence.  The read data set is too big to store in github, so I put it in [our OSF project](https://osf.io/6rgzj/) and added a Makefile rule to download it; see target `shewanella.abundtrim.gz` in Makefile.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b8e7e485ccb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.