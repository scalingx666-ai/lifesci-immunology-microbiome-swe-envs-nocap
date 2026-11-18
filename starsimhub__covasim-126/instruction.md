# Issue

**Title:** Refactor data loaders

## Description

Updates the various data scrapers to create individual case files under the various meta projects:

- corona-data-scraper-project 
- covid-tracking-project                             
- european-centre-for-disease-prevention-and-control

Also, refactored to make things easier to log and test.

Also, added a function `load_neherlab_case_file(path)`, which will read case files from Neher Lab's COVID-19 Scenarios project, stored at 
https://github.com/neherlab/covid19_scenarios/tree/master/data/case-counts

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23024525ba96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.