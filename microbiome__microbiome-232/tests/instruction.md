# Issue

**Title:** Fix Camargo evenness computed on wrong entries

## Description

.

## Problem
`camargo()` in `R/evenness.R` had two problems that together produced wrong values:
- `x[x > 0]` was never assigned, so zeroes were never removed.
- `N <- sum(x > 0)` counts the nonzero taxa, but the loop then read the first `N` *positions* of `x`, zeroes included.

So the index depended on the order of taxa. It was wrong for any sample with a zero before its last observed taxon, which is nearly every real microbiome sample. Examples:

| input | before | after |
|---|---|---|
| issue example, 10 leading zeroes | 1 | 0.1669 |
| issue example, 2 leading zeroes | 0.16685 | 0.16692 |
| `c(0,0,0,5,1,1)` vs `c(5,1,1,0,0,0)` | 1 vs 0.619 | 0.619 vs 0.619 |
| `c(2,2,2,0,2)` (perfectly even) | 0.8125 | 1 |
| all zeroes | error | NA |

## Fix
- Camargo's index is now computed over the observed (nonzero) taxa, with S = number of observed species, as in Camargo (1992). The pairwise sum uses the sorted-abundance identity (O(N log N)).
- The issue's suggested patch removed zeroes when `zeroes = TRUE`, which would invert the documented meaning of that argument. Instead, `zeroes` stays a no-op for camargo, and the docs now say so. It was already a no-op for bulla and evar, and properly removing zeroes would not change their results.
- A sample with a single taxon still returns 1, as the formula gives.

## Verification
- An independent reference implementation agreed on 3000 random vectors, the dietswap data and edge cases.
- New `tests/testthat/test_evenness.R` adds regression tests. The full suite passes (`FAIL 0 | PASS 164`); the 8 warnings are existing ggplot2 `aes_string` deprecations.

## Notes
- **Every Camargo value changes** (dietswap mean 0.195 → 0.139). This is noted in NEWS.
- mia's `.calc_camargo_evenness` has the same bug and needs a separate fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1a308ba4e7f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.