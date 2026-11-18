# Issue

**Title:** Much more stringent consideration of reference genomes

## Description

This PR forces `anvi-reorient-genomes` and its user to be much more careful about the reference genome selection.

Essentially multi-contig references should never be 'rotated' since rotations are basically meaningless if we don't have a biologically meaningful coordinate system, or non-circular genomes :/

Luckily we got a coordinate system error, and this fixes it by not attempting to rotate anything the reference.

I will look into the rotation of the genomes compared to the reference next, which will be a more involved set of changes, but this is pretty safe to merge as it doesn't really do anything (its power is coming from not doing anything :p).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66eeb9557d09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.