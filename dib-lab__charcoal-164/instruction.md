# Issue

**Title:** Add alignment post-processing for stage2.

## Description

This PR adds alignment post-processing to the stage2 workflow.

This is the section of the workflow to mashmap/nucmer alignments into specific recommendations for contig removal, + provide all the necessary information for reporting/output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a669225317ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.