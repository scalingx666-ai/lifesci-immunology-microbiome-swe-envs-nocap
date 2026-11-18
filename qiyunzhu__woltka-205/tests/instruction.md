# Issue

**Title:** Improved handling of range coordinates

## Description

This PR follows #204 by @wasade . It uniformly makes the internal data structure BED-like (0-based, exclusive end), and makes all parsers (BLAST, SAM, PAF) match this standard. The output coverage format is now BED by default. The user can use parameter `--outcov-fmt` to control this behavior. Acceptable values are `bed`, `gff`, `0e`, `1e`, `0i`, and `1i`. Additionally, because the left shift operation is removed, the algorithms are slightly more performant.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58ddd0c10e66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.