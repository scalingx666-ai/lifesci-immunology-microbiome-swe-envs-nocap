# Issue

**Title:** Add support for genome_catalogue annotations in MAP and VIRify

## Description

Changing VIRify and MAP samplesheet generation based on the updates in the relative pipelines

The chunking procedure from the VIRify script has been applied to MAP too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d204342b77d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.