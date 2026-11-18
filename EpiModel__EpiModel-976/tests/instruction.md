# Issue

**Title:** Updates to Package Vignettes

## Description

## Summary

Comprehensive rewrite of all four package vignettes to improve scientific rigor, clarity of communication, and pedagogical utility.

### Intro.Rmd — Full rewrite
- Added "What EpiModel Does" section explaining the three model classes and unified API
- Added a full **network model pipeline walkthrough** (Steps 1–4): network estimation with ERGM terms beyond `~edges`, `netdx` diagnostics with formation and duration plots, multi-simulation epidemic modeling, and analysis including epidemic trajectories, prevalence plots, summary statistics, data extraction, and **transmission tree visualization**
- Added an **extension API teaser** showing a minimal custom SEIR progression module
- Restructured learning pathway to match the Beginner / Intermediate / Advanced tiers on [epimodel.org](https://www.epimodel.org), including references to EpiModelHPC, EpiModelHIV, and EpiModelCOVID

### model-parameters.Rmd — Bug fixes + structural improvements
- **Fixed factual error:** Relative parameter change explanation incorrectly said the function was applied to `act.rate` when it operates on `inf.prob`. Entire paragraph rewritten with correct explanation and inline computed result.
- **Fixed typos:** `dummy.start.param` → `dummy.strat.param`; "combine there results" → "combine their results"
- Added epidemiological motivation (why time-varying parameters matter) in the introduction
- Added note clarifying that scenarios are built on the updater mechanism
- Added inline comments explaining `dissolution_coefs(~offset(edges), 10, 0)` on first use
- Added note explaining why base R plotting is used instead of `plot.netsim()`
- Added cross-references to companion vignettes and prerequisite statement

### network-objects.Rmd — Major expansion (124 → 300 lines)
- **Fixed:** `update_cumulative_edgelist` example showed `truncate = Inf` but actual default is `0`; now clearly documented with implications of each setting
- **Fixed:** "there partners" → "their partners"
- **Added critical prerequisite:** `cumulative.edgelist = TRUE` must be set in `control.net()`
- **New sections:** Network storage modes (tergmLite vs full), accessing network objects during/after simulation using `get_network()`/`set_network()` accessors (not `dat$run$nw`), `get_transmat()`, current edgelists (`get_edgelist`, `get_edgelists_df`, `get_discordant_edgelist`), positional ID vs unique ID, cumulative degree (`get_cumulative_degree`), reachability analysis (`get_forward_reachable`, `get_backward_reachable`)

### attributes-and-summary-statistics.Rmd — Bug fix + content additions
- **Fixed:** Status codes standardized to `"s"`/`"i"` throughout (matching built-in models), replacing inconsistent `"infected"`/`"susceptible"`
- Added `get_core_attributes()` documentation (new in v2.6.0)
- Added concrete positional ID vs unique ID example with table showing departure/arrival
- Expanded `record_raw_object` section with complete access pattern after simulation
- **New:** `epi.by` section with runnable example showing automatic stratified prevalence
- **New:** `mutate_epi()` demonstration
- Added explicit tracker function contract (exactly one argument `dat`, returns scalar)
- Added cross-references and prerequisite statement

## Related

- #977 — Follow-up issue to migrate internal `dat$run$nw` references to accessors (assigned to v2.7.0 milestone)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `abe82de8472a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.