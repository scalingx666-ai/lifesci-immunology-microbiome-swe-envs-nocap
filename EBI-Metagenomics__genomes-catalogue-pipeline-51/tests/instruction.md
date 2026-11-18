# Issue

**Title:** Bugfix/ena metadata

## Description

Added changes to improve location metadata handling for isolates. Added an alternative lookup from API if the XML data retrieval fails and accounted for different possible attribute names of geolocation field in JSON.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dffd7729cfe2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.