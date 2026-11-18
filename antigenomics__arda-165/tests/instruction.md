# Issue

**Title:** Clarify ARDA skill contracts and agent discovery

## Description

Make the repository skill's scientific and pipeline boundaries prominent, and add discoverable agent metadata. The skill distinguishes local junction translation from whole-receptor productivity, retains observed sequence provenance, uses one batched annotation call, and leaves peptide placement in seqtree/project pipelines.

Please review the actual skill changes in this PR. No runtime, defaults, dependency or release changes. Validation: skill metadata validator and diff checks pass; previous master CI and docs passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d7467f0016a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.