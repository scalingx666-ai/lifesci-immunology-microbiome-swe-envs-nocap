# Issue

**Title:** Add --outdir to spacegraphcats command line

## Description

Usage: `python -m spacegraphcats dory-test search extract_reads extract_contigs --outdir=/tmp`

This will put all of the output files under /tmp/.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18d473cdad07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.