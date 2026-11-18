# Issue

**Title:** pseudocount added after compositionality in CLR

## Description

Summary of reasoning: when making a CLR tranformation, transform to compositional before
adding the small v/2 pseudocount to ensure that the prior induced by the
pseudocount is constant across varying library sizes. This is now also mentioned in source documentation.

(This does not fix the issues the constant pseudocounts have, see e.g. https://www.biorxiv.org/content/10.1101/574574v1 but the new behavior will be more predictable if/when used with samples with small total read counts and lots of zeros.)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c76553c71ed8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.