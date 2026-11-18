# Issue

**Title:** Winnowing k > len(seq) > w

## Description

This changes windowed minimizer generation for sequences of length > k but < w.

If the window of minimizers is not full but no minimizers have been generated, bonsai will yield the hash argmin for the window. For example, "AABCD" shingling with k = 3 and w = 8 now yields a single minimizer ("AAB", if the hash function is lexicographic) instead of 0 of them. "AA" still yields an empty sequence of minimizers.

Additionally, we added invertebrate genomes to RefSeq scraping.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5273b81a92eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.