# Issue

**Title:** Enhancements to Monte-Carlo g-formula

## Description

As noted in #73 and #77 there are some further optional enhancements I can add to `MonteCarloGFormula` 

**Items to add:**

- [x] Censoring model

- [ ] Competing risk model

**Testing:**

- [x] Test censoring model works as intended (compare to Keil 2014)

- [ ] Test competing risks. May be easiest to simulate up a quick data set to compare. Don't have anything on hand

The updates to Monte-Carlo g-formula will be added to a future update (haven't decided which version they will make it into)

**Optional:**

- [x] Reduce memory burden of unneeded replicants

I sometimes run into a `MemoryError` when replicating Keil et al 2014 with many resamples. A potential way out of this is to "throw away" the observations that are not the final observation for that individual. Can add option `low_memory=True` to throw out those unnecessary observations. User could return the full simulated dataframe with `False`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3461b3319361`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.