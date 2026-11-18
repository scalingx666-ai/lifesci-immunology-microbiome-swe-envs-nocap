# Issue

**Title:** v1.1.1 updates

## Description

Fixed:
- Early exit logging bug
- Adding error logging for some modules

New Features:
- Taxonomic Profiles tables as output with new arguments `--species-threshold` and `--subspecies-threshold`
- Check fir consistent thresholds before combining tax profiles
- argument `-mmK`/`--minimap2-K` for minimap2 `-K` (minibatch size) to control memory usage
- making '50M' default `-mmK`

Docs:
- Added tax profile info to Docs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f9fb9ff1a30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.