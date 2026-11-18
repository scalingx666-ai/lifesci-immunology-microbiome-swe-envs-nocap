# Issue

**Title:** Fixing gunicorn

## Description

both `gunicorn` run from `Dockerfile.dash` and `python src/dash_app.py` work in this PR. 

this is necessary for Heroku deploy.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `963f6f16f409`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.