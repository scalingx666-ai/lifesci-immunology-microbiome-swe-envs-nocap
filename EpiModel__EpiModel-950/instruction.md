# Issue

**Title:** Prepare v2.5.5 for CRAN submission

## Description

- Update NEWS.md heading from 2.5.1 to 2.5.5 and add missing changelog entries (plot.dcm fix, integer attributes, lintr cleanup)
- Update README.md version badge from 2.5.0 to 2.5.5, fix http->https
- Restore options(scipen) via on.exit() in comp_plot.icm and comp_plot.dcm to comply with CRAN policy on preserving global state
- Remove unnecessary Sys.sleep(4) in crosscheck.net; warning is sufficient

https://claude.ai/code/session_018ubYQqj6m7vEMeZP4J1Y9F

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `064c07660758`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.