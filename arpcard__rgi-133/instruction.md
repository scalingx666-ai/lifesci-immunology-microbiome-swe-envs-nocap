# Issue

**Title:** Update Dockerfile to latest and tidy README

## Description

- Dockerfile is updated to install directly from the repo (so should always be the latest version)
- Dockerfile now uses auto_load
- Removed a couple of deprecated dependencies from the README and tidied up requirements.txt
- Added conda env install for all the non-python deps (ideally to be kept synched with the actual conda package)
- Tidied up install section of README
- Moved table of contents further up as navigation was getting hard.
- Split long demo commands to make README easier to read.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6358c834fdf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.