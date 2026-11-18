# Issue

**Title:** Clean and update pathogen sheet

## Description

## Cleaning pathogen sheet

This PR cleans the pathogen sheet in the following ways:

- Update organism names to match latest version on NCBI, placing the old name in "alternative_names" if altered
- Removes trailing commas in some pathogenic sites
- Standardize names for non-human hosts (e.g., "porcine" in place of "swine" and "porcine")
- Fix capitalization inconsistency for host values
- Sort the host values alphabetically

## Updating pathogen sheet

- Addition of 251 additional pathogens entries based on a literature review of abstracts available on PubMed

This improvements were implemented using antigravity.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8be35804fb2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.