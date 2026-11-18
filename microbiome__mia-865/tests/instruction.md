# Issue

**Title:** Fix/unifrac sum bug

## Description

.

`Assay::get_sample_counts()` accumulated each sample's total in an `unsigned int`, so the total was the sum of the integer parts of the abundances: exact for counts, 0 for relative abundances, too small for percentages. Striped UniFrac divides by these totals to turn tips into proportions, so weighted UniFrac was NaN on relative abundances and silently wrong on percentages, and unweighted UniFrac was wrong on relative abundances. Declaring the accumulator `double`, as upstream UniFrac does in `biom_inmem::compute_sample_counts()`, fixes it. The accumulator dates from 172c1931 (#697), but Faith PD does not normalise, so it never used the totals. The bug reached users with e5b393fc (#829).

**Changes**
- `src/assay.cpp`: `unsigned int sum` → `double sum`.
- `tests/testthat/test-5Unifrac.R`: new test on a three-tip tree that computes weighted and unweighted UniFrac from counts, relative abundances and percentages and checks each against the hand-computed values (5/3 and 1/2). The proportions are thirds, so the integer parts of the percentages sum to 99 and the percent case is caught too. Before the fix, 3 of its 6 expectations fail. It takes about 0.2 s and does not need `ecodive`.
- `NEWS`, `DESCRIPTION`: entry and version bump to 1.21.15.

**Checks** (old and fixed code installed into separate scratch libraries, R 4.6.1)

Maximum absolute difference from `ecodive` on `GlobalPatterns` (650 off-diagonal cells):

| assay | weighted, before | weighted, after | unweighted, before | unweighted, after |
|---|---|---|---|---|
| counts | 2.2e-14 | 2.2e-14 | 2.7e-15 | 2.7e-15 |
| relabundance | all 650 NaN | 4.7e-14 | 0.196 | 2.7e-15 |
| percent | 8.41 | 5.9e-14 | 2.7e-15 | 2.7e-15 |

- `test-5Unifrac.R` passes (20 expectations, 0 failures); before the fix the new test fails 3 of 6.
- `test-0diversity.R`, `test-5getDissimilarity.R`, `test-getPERMANOVA.R` and `test-addMDS.R` pass. Faith PD shares `Assay` but calls `set_proportions(normalize = false)`, so it never used the totals and is unaffected.

<details>
<summary>Comparison script</summary>

```r
library(mia)
data("GlobalPatterns", package = "mia")
gp <- transformAssay(GlobalPatterns, method = "relabundance")
assay(gp, "percent") <- assay(gp, "relabundance") * 100
ref <- list(
    "TRUE" = as.matrix(ecodive::weighted_unifrac(
        t(assay(gp, "counts")), rowTree(gp))),
    "FALSE" = as.matrix(ecodive::unweighted_unifrac(
        t(assay(gp, "counts")), rowTree(gp))))
for (w in c(TRUE, FALSE)) for (a in c("counts", "relabundance", "percent")) {
    d <- as.matrix(getDissimilarity(
        gp, method = "unifrac", weighted = w, assay.type = a))
    diff <- abs(d - ref[[as.character(w)]])
    cat(sprintf("weighted=%-5s %-12s NaN=%-4d max|diff|=%.3g\n",
        w, a, sum(is.nan(d)), max(diff, na.rm = TRUE)))
}
```

</details>

Description generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91617566e9a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.