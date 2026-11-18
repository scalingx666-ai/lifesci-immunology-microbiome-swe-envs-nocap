# Issue

**Title:** Predict longitudinal labels at every timepoint in ep.ml

## Description

`ep.ml.Task(rolling=True)` predicts a longitudinal variable such as the hourly PhysioNet 2019 sepsis label at every timepoint from the timepoints before it, with summary models fit per timepoint and models of time series predicting causally in one pass, predictions in `obsm[key]` of shape (n_obs, n_t), and evaluate, calibration, conformal prediction, importance and plots working on them with a patient bootstrap. On held-out PhysioNet 2019 patients, the GRU reaches an hourly sepsis AUROC of 0.75 (AUPRC 0.05) and gradient boosting 0.67 (AUPRC 0.02).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2888f35546b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.