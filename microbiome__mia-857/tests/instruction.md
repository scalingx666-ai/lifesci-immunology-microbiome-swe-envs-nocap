# Issue

**Title:** Fix/optimize multiple alpha index rarefaction

## Description

Calculate all alpha indices from shared rarefaction rounds (#855)

. Builds on #854, which fixes the averaging step reused here; please merge #854 first. Until then the diff here also shows #854's four commits.

With `niter` set, `getAlpha()` looped over the indices, and each index called `.alpha_rarefaction()`, which rarefied the data `niter` times. Asking for k indices therefore rarefied the data k × `niter` times, and rarefaction is the expensive step. Now `.alpha_rarefaction()` rarefies once per round and calculates every requested index from that round's data, so the data is rarefied `niter` times in total.

**Changes**
- `R/addAlpha.R`:
  - `getAlpha()` no longer loops over the indices itself. When rarefying it passes all indices to `.alpha_rarefaction()`; otherwise it passes them to a new helper, `.calculate_alpha_indices()`, which holds the old loop.
  - `.alpha_rarefaction()` rarefies once per round and calls `.calculate_alpha_indices()` on the rarefied data.
  - `name` must now be unique. Rounds are averaged by column name, so two indices sharing a name would be averaged together. The check applies with and without rarefaction; before, duplicate names returned columns `a` and `a.1`.
  - One sentence added to the rarefaction docs.
- `man/addAlpha.Rd`: regenerated.
- `tests/testthat/test-addAlpha.R`: new test that asks for `observed` twice under two names and checks that both columns are identical, which holds only if they come from the same rounds. It also checks the error for duplicate names. Both expectations fail before this change.
- `NEWS`, `DESCRIPTION`: entry and version bump to 1.21.13.

**Behaviour**
- Without rarefaction the output is identical to before.
- With rarefaction, each index is still the mean over `niter` rounds, but the indices now share draws instead of each getting its own. Values for every index except the first therefore differ from before, even with a fixed seed.
- When rarefying, `BPPARAM` now runs the rounds in parallel instead of the indices. Without rarefaction the indices still run in parallel. With `niter = 1` the rarefied path is a single task, but it is still faster than before (see the timings).
- Rarefying with `SnowParam` failed before, because the old code nested `bplapply()` calls on the same `BPPARAM`; it now works. With an `RNGseed`, results are now identical across `SerialParam`, `SnowParam` and `MulticoreParam`.
- The "samples were dropped" warning is given once instead of once per index.

**Timings** (GlobalPatterns, `sample = 10000`, median of 3 runs, "before" is #854)

| | serial, before | serial, after | 4 workers, before | 4 workers, after |
|---|---|---|---|---|
| 4 indices, `niter = 1` | 0.93 s | 0.29 s | 0.60 s | 0.44 s |
| 4 indices, `niter = 10` | 9.35 s | 2.48 s | 1.76 s | 1.19 s |
| 8 indices, `niter = 1` | 1.76 s | 0.35 s | 1.03 s | 0.61 s |
| 8 indices, `niter = 10` | 16.89 s | 3.53 s | 3.45 s | 1.49 s |

The 4 indices are shannon, observed, chao1 and pielou; the 8 add gini_simpson, ace, dbp_dominance and hill. Workers are `MulticoreParam(4)`.

<details>
<summary>Timing script (MulticoreParam needs Linux or macOS)</summary>

```r
library(mia)
library(BiocParallel)
data(GlobalPatterns, package = "mia")
index4 <- c("shannon", "observed", "chao1", "pielou")
index8 <- c(index4, "gini_simpson", "ace", "dbp_dominance", "hill")
time <- function(index, niter, BPPARAM){
    median(replicate(3, system.time(getAlpha(
        GlobalPatterns, index = index, sample = 10000, niter = niter,
        BPPARAM = BPPARAM))[["elapsed"]]))
}
for (index in list(index4, index8)) for (niter in c(1, 10)) {
    cat(sprintf("%d indices, niter = %2d | serial %5.2f s | 4 workers %5.2f s\n",
        length(index), niter, time(index, niter, SerialParam()),
        time(index, niter, MulticoreParam(4))))
}
```

</details>

`test-addAlpha.R` passes locally (52 expectations, 0 failures). I also checked that the rarefied output equals rarefying each round by hand with `rarefyAssay()`, calculating every index on it and averaging.

PR report generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e65c510856f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.