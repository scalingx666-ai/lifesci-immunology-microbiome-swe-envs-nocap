# Issue

**Title:** More consistently rename RPKM to abundance

## Description

* RPKM is more obscure, technical terminology
* It's technically wrong, since we don't require the abundance to be expressed in terms of reads per kilobase per million mapped reads.
* We call the output file `abundance.npz`
* "Abundance" is the standard terminology for this feature in the literature

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c049fbd01783`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.