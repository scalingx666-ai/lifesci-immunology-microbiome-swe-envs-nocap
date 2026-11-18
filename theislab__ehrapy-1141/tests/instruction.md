# Issue

**Title:** Make ehrapy discoverable for search engines and coding agents

## Description

The README, docs landing page and PyPI metadata now say what ehrapy is for and which data it reads, with a quickstart that clusters all PhysioNet 2012 ICU stays and tests which measurements differ between patients who died and survived. The docs also ship a sitemap, an llms.txt, canonical URLs to the stable version and a CITATION.cff, so search engines and coding agents land on one current description.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf31015a0972`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.