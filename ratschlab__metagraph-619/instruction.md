# Issue

**Title:** Validate diff-assembly JSON has 'groups' array

## Description

Missing or empty 'groups' silently produced an empty output (no error, no fasta) — impossible to debug from the user side. Now errors out with the expected schema.

Add an integration test for the malformed-config case and an inline schema skeleton + `shared_labels` description to the docs alongside the linked examples.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7a4a0ae0a5f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.