# Issue

**Title:** Align the signature and ancillary default of weibull_aft with log_logistic_aft

## Description

`ep.tl.weibull_aft` takes `event_col` as keyword argument and defaults to `model_ancillary=False` like `ep.tl.log_logistic_aft`, which changes the fitted models of calls that relied on the old default.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79bd3866cb38`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.