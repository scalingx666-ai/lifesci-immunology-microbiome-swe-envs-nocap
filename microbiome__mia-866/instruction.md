# Issue

**Title:** Fix Camargo evenness computed on wrong entries

## Description

## Problem
`.calc_camargo_evenness()` had the same bug as microbiome/microbiome#231, which was fixed there in microbiome/microbiome#232. It took `N <- colSums2(mat > 0)`, the number of nonzero features, and then looped over the first `N` *rows* of each column, zeroes included. So the result depended on feature order and was wrong for nearly every real sample.

| input | before | after |
|---|---|---|
| issue example (10 leading zeroes) | 1 | 0.1669 |
| `c(5,1,1,0,...)` vs the same values reversed | 0.619 vs 1 | 0.619 vs 0.619 |
| `c(2,2,2,0,2)` (perfectly even) | < 1 | 1 |
| esophagus samples B, C, D | 0.694, 0.623, 0.801 | 0.287, 0.374, 0.253 |

## Fix
- Camargo's index is now computed per sample over the observed (nonzero) features, with S = number of observed species, as in Camargo (1992). The pairwise sum uses the sorted-abundance identity (O(N log N)).
- A sample with no observed features returns NA.
- The fixed function matches a brute-force `outer()` reference on esophagus and on the edge cases.

## Test fix
In `test-5evenness.R` the camargo expectation was `round(c(...)), 7)`. That rounded the expected values to integers and passed `7` as `tolerance`, so the test passed for any value. The expectation now uses the correct values, and regression tests for the cases above are added. `test-5evenness.R` and `test-addAlpha.R` pass locally, including the DelayedArray path (16 and 75 expectations). The full test suite was not run.

**Every Camargo value changes.** NEWS has an entry and the version is bumped to 1.21.15.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d241b007c695`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.