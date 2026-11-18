# Issue

**Title:** Add exact mixed codon-origin posteriors

## Description

Add exact local G/P/N codon-origin distributions and immutable template constraints to the existing masked generation engine. Mixed codons retain their genetic-code possibilities without treating immutable germline or P bases as mutations; single- and tandem-D histories remain summed exactly. Ordinary Pgen, joint N intervals and all bundled model assets remain unchanged.

Validation: 1,887 release-tier Python tests pass (92.70 s); both C++ tests pass; strict Sphinx documentation and focused Ruff checks pass. Origin checks cover complete posterior partitions, pure-N marginal agreement, immutable letters, P boundaries, synonymous-only N variation, unsupported custom metadata and thread equality.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aaa27fa5f0fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.