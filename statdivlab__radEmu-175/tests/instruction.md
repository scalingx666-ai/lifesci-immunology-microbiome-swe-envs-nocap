# Issue

**Title:** Speed up null fitting for categorical X's via Fisher scoring + line search

## Description

The goal here is not to have a general faster fitting but some major speed ups for the common case of categorical covariates and pseudoHuber median g(.). 

It turns out that #90 is impossible (no closed form for pH median g(.)), but we can speed things up. 

I'm seeing perhaps 1000x faster, basically instantaneous fitting, but I haven't broadly tested it over a range of p and J. (n doesn't matter here) 

In the one case I investigated where estimates differ from `fit_null`, this approach had higher likelihood and it strictly enforces the g constraints (ie constraint_tol is trivially 0). 

What's it actually doing? Fisher scoring (in the free parameters) + a line search to ensure the likelihood is increasing at each step. 

Lots of ChatGPT here, which is fine because I know what I want. 

Not ready for review, but opening to give some updates to @svteichman 

Next steps (AW) - taken from my notes in  fit_null_discrete

```
  ## Currently this works for 
  #### two groups with X's (1, 0) and (1, 1)
  #### testing the first column, last column also constrained
  
  #### it is equivalent to fit_null with k_constr=2, j_constr=1, j_ref=J,
  
  ## It needs to be generalized to consider 
  #### multiple categories (can we assume identity-like then back transform? is this constraint and likelihood-preserving?) 
  #### different columns for testing
  #### the same inputs as fit_null and comparable convergence statistics
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0f8b76f2518`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.