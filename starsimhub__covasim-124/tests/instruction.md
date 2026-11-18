# Issue

**Title:** US Census Data

## Description

Motivation:
  - We need state by state age demographics.

Related Issues:
  - InstituteforDiseaseModeling#47

Changes:
  - Pulled down US census data localy altered it and saved it to pickle
    format
  - added `get_us_stage_age_distribution` method to loaders

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98e4071d9a9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.