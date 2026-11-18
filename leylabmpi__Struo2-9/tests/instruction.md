# Issue

**Title:** Fix handling of non-gzipped genome files

## Description

Fixed kraken2_rename_genome.py to only decode lines of the genome file if the file was gzipped. If the file was not gzipped then the lines of the file will be strings,  and so attempting to decode will raise an exception.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15a22fff3f97`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.