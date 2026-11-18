# Issue

**Title:** Household Size by Country

## Description

Motivation:
  - Set the average household size for a location based on UN population
    data https://population.un.org/Household/index.html#/countries/840

Related Issues:
  - #120

Changes:
  - Pulled in avg house household data from the UN and store locally.
  - Helper function to get the requested country.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `571000b2029f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.