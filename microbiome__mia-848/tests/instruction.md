# Issue

**Title:** Align method = 'log' with log2 and log10 in transformAssay

## Description

. Aligns `transformAssay(..., method = "log")` to compute the natural logarithm (base e) natively with pseudocount support, ensuring consistency with `"log2"` and `"log10"`. Retains access to `vegan::decostand(method = "log")` under `method = "log.decostand"` (and alias `"log_decostand"`), updates documentation, and adds unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a43428fb3283`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.