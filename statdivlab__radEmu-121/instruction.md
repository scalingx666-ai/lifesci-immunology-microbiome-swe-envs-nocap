# Issue

**Title:** Adding a test to PR 120 for large p

## Description

Adding test for optimize rows PR #120  to compare when the new `optimize_rows` is and isn't used for large p. This test is skipped by default because in practice it takes more than 10 minutes. The results of this test with large p (p = 8) is that the new approach is faster and has a lower estimation error for the true B compared to the old approach. There is a maximum difference between estimates of 0.04, which has a similar magnitude to the maximum estimation error between the old approach and the true B. The maximum difference between estimates in the new approach and the true B is less than 0.01. The mean estimation error is also smaller for the new approach (with `optimize_rows = TRUE`) than with the old approach. This test can be run manually, but is skipped in automated testing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b0b02bcad8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.