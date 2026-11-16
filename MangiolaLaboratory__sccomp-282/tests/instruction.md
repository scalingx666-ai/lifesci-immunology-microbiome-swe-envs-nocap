# Issue

**Title:** Make `sccomp_remove_outliers()` deterministic with fixed `mcmc_seed`

## Description

`sccomp_remove_outliers()` could return different outlier classifications across repeated calls on the same fitted object, even with fixed `mcmc_seed` and `cores = 1`. Root cause was incomplete seed propagation to stochastic generated-quantities steps used for posterior predictive outlier detection.

- **Seed propagation in outlier detection pipeline**
  - Updated `R/sccomp_remove_outliers.R` to pass `seed = mcmc_seed` into **both** `generate_quantities` calls (`rng` and `rng2`).
  - This aligns all stochastic steps in `sccomp_remove_outliers()` with the public reproducibility contract of `mcmc_seed`.

- **Regression coverage for reproducibility**
  - Consolidated reproducibility tests into a generic script: `tests/testthat/test-reproducibility.R`.
  - The script now includes:
    - reproducibility for `sccomp_estimate()` with fixed `mcmc_seed`,
    - reproducibility for `sccomp_remove_outliers()` with fixed `mcmc_seed`.
  - Extended both reproducibility tests to run under **both** fitting algorithms:
    - `inference_method = "pathfinder"`,
    - `inference_method = "hmc"`.
  - Removed `tests/testthat/test-sccomp_remove_outliers-reproducibility.R` after consolidation to avoid test fragmentation.

```r
rng = mod_rng |> sample_safe(
  generate_quantities_fx,
  attr(.estimate, "fit")$draws(format = "matrix"),
  data = ...,
  parallel_chains = ...,
  threads_per_chain = cores,
  seed = mcmc_seed,
  sig_figs = sig_figs
)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18a4be86f649`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.