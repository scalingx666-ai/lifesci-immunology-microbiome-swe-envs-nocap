# Issue

**Title:** Fix MCMC.maxchanges = Inf integer coercion warning in tergm

## Description

Replace MCMC.maxchanges = Inf with .Machine$integer.max in netdx(), control.net(), and netest() defaults.

When Inf is passed as MCMC.maxchanges, it flows to tergm::tergm_MCMC_slave() which calls as.integer(maxchanges) before the .Call to MCMCDyn_wrapper. as.integer(Inf) produces NA with a warning: "NAs introduced by coercion to integer range".

Note that tergm wraps the analogous MCMC.maxedges parameter with deInf(maxedges, "maxint") before as.integer(), which correctly converts Inf to .Machine$integer.max. The same deInf() wrapper is missing for MCMC.maxchanges in tergm_MCMC_slave(). This is arguably a bug in tergm -- see the relevant code:

  tergm::tergm_MCMC_slave:
    maxedges <- NVL(control$MCMC.maxedges, Inf)
    maxchanges <- control$MCMC.maxchanges
    z <- .Call("MCMCDyn_wrapper", ...,
              as.integer(deInf(maxedges, "maxint")),  # <- wrapped
              as.integer(maxchanges),                  # <- NOT wrapped
              ...)

This warning surfaced after ergm 4.12.0 (2026-02-17) triggered a recompilation of the tergm binary, likely changing how the C code uses the maxchanges argument.

Using .Machine$integer.max (2,147,483,647) is functionally equivalent to Inf for this purpose -- it effectively removes the limit on MCMC changes per step -- while avoiding the integer coercion warning.

* Related to 
* Issue for tergm filed at

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3db8909ef216`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.