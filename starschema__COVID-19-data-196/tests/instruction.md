# Issue

**Title:** Airflow add env var

## Description

- added GIT_USER, GIT_TOKEN as env variable to airflow.yml and as papermill variable to covid_etl_dag.py
- added ENVIRONMENT variable to check when running qa_checks function
- fixed NYC_HEALTH_TEST notebook

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3c8720d1157`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.