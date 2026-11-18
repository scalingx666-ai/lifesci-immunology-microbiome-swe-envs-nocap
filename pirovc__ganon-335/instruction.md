# Issue

**Title:** Feature/improve genome size est

## Description

Improved genome size estimations based on assembly sizes, either from assembly_summary or eutils

New option: `--genome-size` 
 - New default: `--genome-size auto` 
 - Old behavior: `--genome-size standard` 
 - New option:  `--genome-size assembly-custom` 
 - `--skip-genome-size` is replaced with `--genome-size skip`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e875caf45b3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.