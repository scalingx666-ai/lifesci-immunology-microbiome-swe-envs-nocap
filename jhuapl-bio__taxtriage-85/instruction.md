# Issue

**Title:** 2.20.2025 updates to pathogen sheet

## Description

Updated pathogen sheet:

- Removed Fusarium oxysporum alternavirus 1
- Removed Aspergillus fumigatus partitivirus 2
- Added Aspergillus fumigatus and Fusarium oxysporum as opportunistic pathogens
- Fixed weird symbols in naming column
- Reverted Mycobacterium gadium to Mycobacterium avium
- Reverted Prevotella oris to Prevotella corporis
- Removed duplicate entries

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `249a97f5fcde`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.