# Issue

**Title:** Add a net-controls help page for ergm and tergm control settings

## Description

.

Most of the material from that thread now lives in the SISMID appendix, [Improving Model Estimation and Simulation](https://epimodel.github.io/sismid/11_advanced/mod11-NetFitting.html). This adds the package side: one reference help page, plus links to the appendix for the worked examples.

- New `?net-controls` page. `?set.control.ergm`, `?set.control.tergm`, and `?set.control.ergm.ego` now open it, which was the original complaint in the issue. It covers which control function each argument takes at each stage, the `MCMC.maxchanges` default that gets dropped when you pass your own `set.control.tergm`, how to use static vs. dynamic `netdx()` to tell whether the per-step burn-in, the EDA, or the ERGM fit needs adjusting, and the short list of settings we actually change. The example runs in under a second.
- `netest()`, `netdx()`, `control.net()`, and the package page now point to it. I also dropped the "> 25 time steps" threshold from the `edapprox` param, since the appendix shows bias at duration 25.
- The Intro vignette links the page and the appendix. I also changed the NME course labels there to module ranges, since the old chapter numbers were out of date.
- pkgdown reference index and NEWS.

One check behind the wording: on an edapprox fit at duration 10 (Steve's N = 1000 model), fixing the per-step burn-in at 1e4 in `netdx()` cut the edges bias from -3.6% to -1.7%, but concurrent moved from +3.2% to +6.8%. So the page treats burn-in as the cheap first check and the full STERGM as the fix when bias remains.

Steve's draft vignette on the `tergm-control-doc` branch isn't merged here, since that content moved to the appendix.

`R CMD check --as-cran` is clean (Status: OK).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1eab068ceb0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.