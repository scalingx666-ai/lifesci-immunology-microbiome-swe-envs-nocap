# Issue

**Title:** Update docs on heuristics used by charcoal

## Description

See [this section](https://github.com/dib-lab/charcoal/tree/fix_docs_again/doc#how-charcoal-finds-contamination) - how charcoal finds contamination - in doc/README.md

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f46560f0bc3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.