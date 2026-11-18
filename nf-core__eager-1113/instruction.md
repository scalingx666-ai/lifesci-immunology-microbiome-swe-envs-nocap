# Issue

**Title:** Update Metagenomics Test-Datasets

## Description

## PR checklist

The following tool run w/o failing and produce meaningful output-tables

- [x] MALT
- [x] Krakenuniq
- [x] Kraken2
- [x] Metaphlan4

After the #1098 is merged, we should also include test-data for paired input for

- [ ] MALT (not supported for PE)
- [ ] Krakenuniq
- [ ] Kraken2
- [ ] Metaphlan4

(or make this a separate PR)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `059c33a611b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.