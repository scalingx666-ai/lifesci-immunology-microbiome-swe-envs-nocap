# Issue

**Title:** Prepare 5.3.1 with batched exact cohort distances

## Description

Prepare 5.3.1 with batched exact cohort distances. F/F2/D/Jaccard use one shared sparse clonotype vocabulary for four or more samples. Up to three samples retain direct joins to avoid global encoding overhead for a few deep repertoires. Count-scale accumulation improves numerical stability; centered Pearson, noncanonical count types and unsafe totals retain existing arithmetic. Known numerical/output allocations are checked, and result columns are constructed natively.

Validation: 131 combined signature/overlap checks pass (two deselected), and strict Sphinx passes. Three-repeat full API medians on 64 synthetic samples × 1,000 clonotypes (2,016 pairs, single-thread kernels) improve the four metrics 17.6–19.7x, with maximum distance differences 4.44e-16 for F/F2 and zero for D/Jaccard. Three samples × 10,000,000 distinct clonotypes retain existing performance (3.53 vs 3.52 seconds) and identical results. F2 matrix bytes also match with preinitialized Polars pools of 1 and 4 threads.

The new explanation page derives identities, numerical bounds and resource costs; the how-to guide stays concise. No model or native-kernel changes. The branch includes current dev, including the independently merged bounded-memory corpus-hashing fix. Updated-head CI must pass before integration/publication.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2fb0a517b567`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.