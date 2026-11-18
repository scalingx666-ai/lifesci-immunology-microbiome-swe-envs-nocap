# Issue

**Title:** Dash config-and-context

## Description

### Cleaning up
---
- Moved contents of run.py to chime_dash/__init__.py
- Delete run.py

### Facilitating contributions
---
- Add create_app function to chime_dash
- Returns Env, App
- App class is the dash instance, Env holds the context specific config settings
- Basic exception for invalid context selection
- defaults to production
- room to expand as needed
- Add instructions for using to dash_app.py docstring for contributor visibility 
- tested on Heroku

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `677f96c87152`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.