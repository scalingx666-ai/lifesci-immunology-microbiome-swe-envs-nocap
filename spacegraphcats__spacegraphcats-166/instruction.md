# Issue

**Title:** [MRG] optimize minhash db construction by removing unnecessary intermediate step

## Description

Prior to this PR, `search.make_catlas_minhashes` first constructed a minhash for each cDBG node, then combined those into minhashes for each leaf node in the catlas.  This was done for simplicity, but the cDBG node minhashes aren't saved or used. This PR changes minhash construction so that the catlas leaf node minhashes are built directly from the contigs.  This should result in a significant memory savings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bcfa73a105be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.