# Issue

**Title:** remove biolib,mpld3,jinja dependencies. Fix bug classify case

## Description

In one special situation ( a userleaf has no closest pplacer genome, has close genomes detected by fastani but the closest genome is less the FASTANI_SPECIES_THRESHOLD percentage ) the other_related_references field required a pplacer_leafnode that didn't exist. ( line 678 of classify.py)
This has been fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b28a31ef9fc3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.