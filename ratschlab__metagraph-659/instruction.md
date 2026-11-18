# Issue

**Title:** Batch and share row-diff column reconstruction

## Description

Column extraction reconstructs rows one at a time, repeating shared paths. Share the scan across binary, count and tuple row-diff matrices, avoid copying returned rows, and reconstruct 32 rows per batch using the existing batch helper.

This preserves graph iteration order and index formats. Batching uses more temporary memory for decoded rows and their shared reconstruction paths; the limit is 32 requested rows, not a fixed byte budget.

Focused tests cover masked graphs, partial batches, signed count differences, coordinate shifts and serialization. Local synthetic column-query benchmarks across all three matrix types were 1.5–10.6× faster; these are not whole-application measurements.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e97d24abf9e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.