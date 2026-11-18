# Issue

**Title:** Feat/binning transformation

## Description

Adds a quantile based binning transformation to the mia::transformAssay() -function, as discussed in #800 
Default value of bin = 4, reflects roughly division to "rare, low, medium, high" which is easy to understand.
Unit tests include checks for both sample- and feature-wise transforms. 

Should the transformation default to using "relabundance" assay, or leave choice to user discretion?

Pending tasks:
- [x] Add documentation
- [ ] Add information on binning transformation to OMA


Potential optimizations;
- Adding a parallel version, with e.g. doFuture, can be beneficial for large datasets. 
- C++ implementation called with Rcpp would be even better, both for serial and parallel performance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6230daf7c5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.