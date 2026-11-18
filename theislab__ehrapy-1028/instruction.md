# Issue

**Title:** Adjusted survival curves

## Description

**Description of changes**
 
Implemented covariate-adjusted survival curves for CoxPH models with two new functions `ep.tl.cox_ph_adjusted_curves()` and `ep.pl.cox_ph_adjusted_curves()`, similar to the functionality of `surv_adjustedcurves() `/ `ggadjustedcurves()` from R's survminer package. Based on adjusted survival curves paper: (https://cran.rproject.org/web/packages/survival/vignettes/adjcurve.pdf).

**Technical details**

`ep.tl.cox_ph_adjusted_curves()`
- Accepts a fitted CoxPHFitter (returned by tl.cox_ph()) directly as a parameter
- Supports two methods: average (population-averaged curves per group with bootstrapped CIs) and conditional (single synthetic reference patient with covariates fixed at mean/mode)

`ep.pl.cox_ph_adjusted_curves()`
- Visualizes output of tl.cox_ph_adjusted_curves() using holoviews

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `077f4ee96609`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.