# Issue

**Title:** Add prefix to final bin name

## Description

Small PR to add the possibility to add a prefix to the final bin names as requested in #61 . 

The prefix is used to name the final bins using this pattern : `<prefix>_bin<bin_id>` 
This name is used to name the fasta bin file and in the name column of the result file. 
By default the prefix is `binette`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98a732ba9bc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.