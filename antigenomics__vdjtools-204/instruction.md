# Issue

**Title:** Release vdjtools 5.2.1 with exact source-preserving tcR ingestion

## Description

## Behavior

Accept tcR `bestVGene` / `bestJGene` aliases in MiTCR-format tables. Add `read_mitcr(..., collapse=False)` for identity-aware consumers: preserve source row order, repeated receptors, ambiguous/missing gene calls and source counts. Historical bulk filtering/collapse remains the default. Source-preserving counts are parsed as exact nonnegative int64 values; already-integer values avoid the shared normalizer's floating-point path.

This is the ingestion prerequisite for antigenomics/vdjmatch#41. Released vdjtools 5.2.0 lacks these capabilities. The branch reconciles the already released master ancestry without changing native Pgen code or bundled models.

## Verification

All 50 conversion tests and 16 existing IO/schema tests pass, including tcR aliases and the source-preserving versus default-collapse contract. Release packaging and an owner-approved release remain prerequisites for the downstream released-dependency check. The author approved the dependency release after green CI; metadata is now 5.2.1. No release has yet been published.

The final 5.2.1 wheel was installed with declared dependencies in a clean Python 3.13 environment and verified on repeated rows, missing/ambiguous genes and exact counts above 2^53. Native code and model assets remain unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ac89a6d4082`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.