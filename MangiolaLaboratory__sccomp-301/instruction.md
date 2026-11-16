# Issue

**Title:** Add sccomp_simulate() on the current model; deprecate simulate_data()

## Description

Rebuilds the simulation feature of #254 on the current model, with the same interface. #254 itself can no longer be merged: it is 176 commits behind and targets the old `prec_coeff` parameterisation with two random-effect slots.

`simulate_data()` on `master` does not work against current fits. Its R code fails while reshaping the coefficients (`Can't find column cell_group`), and its Stan model reads `prec_coeff`, `beta_raw_raw` and `random_effect_raw`, none of which the current fit produces.

## Interface (as in #254, with the current argument style)

```r
sccomp_simulate(fit, formula_composition, formula_variability = NULL, new_data = NULL,
                coefficients = NULL, mean_dispersion_slope = NULL, mean_dispersion_intercept = NULL,
                sample = NULL, cell_group = NULL, variability_multiplier = 1, number_of_draws = 1,
                mcmc_seed, cores, sig_figs = 9, cache_stan_model, variability_scatter = TRUE)
```

- `coefficients`: a table with one row per cell group and one column per design column. Each design column must sum to zero across cell groups, and design columns that are absent are set to zero. If `NULL`, the posterior coefficients are used.
- `mean_dispersion_slope` and `mean_dispersion_intercept`: the model now has one slope and intercept per variability term, so each argument takes either one number, applied to every term, or a vector named by term (e.g. `c(typecancer = 2)`). Terms that are not named keep their posterior values. Overriding the slope alone fixes that term's intercept at its posterior mean, as in #254.
- `sample` and `cell_group` are character strings, as in `sccomp_estimate()`, and are taken from the fit when `NULL`. #254 used the older `.sample` / `.cell_group` / `.coefficients` tidy-eval arguments, which are not part of `sccomp_simulate()`.
- `simulate_data()` is deprecated, keeps its legacy signature, and calls the same code. The `.coefficients` column form still works there. The default `variability_multiplier` changes from 5 to 1.

## Model

Variability comes from the abundance coefficients rather than the posterior `alpha`, as in #254. For each variability term, `alpha = beta[map] * slope + intercept`, using the first component of the association and the variability-to-composition map. A fit made with `exclude_mean_variability_association = TRUE` uses a slope of 0. By default (`variability_scatter = TRUE`), each cell group's variability is also drawn around that trend with the posterior residual SD (`prec_sd`), as fitted cell groups scatter around it. #254 left this scatter out, and `variability_scatter = FALSE` restores that behaviour. The Stan model mirrors the fitted parameter block, including all six random-effect slots, and `prepare_replicate_data()` builds the designs, so sub-formulas, random effects and smooths are handled the same way as in `sccomp_replicate()`. Simulating with an intercept from an intercept-free fit is rejected with an error.

## Tests

`tests/testthat/test-simulate_data.R` ports the cases from #254 and adds numeric checks:
- the simulated `alpha` equals `beta * slope + intercept` exactly;
- a named override changes only its own term;
- an excluded association simulates with slope 0;
- with scatter on, deviations from the trend match the fitted `prec_sd`;
- simulated proportions match `softmax(X * beta)` within 0.005;
- the same seeds give identical counts;
- a model with random effects simulates;
- invalid coefficients produce errors.

All pass locally with `NOT_CRAN=true`, and `test-replicate_data.R` still passes.

The version is bumped to 2.5.4 (2.5.3 is the design-matrix reporting already on master), so the compiled-model cache does not reuse the old simulation binary.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `564b0c83ebce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.