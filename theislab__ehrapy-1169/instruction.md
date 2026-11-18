# Issue

**Title:** Fix papercuts in ep.ml calibration, subgroup order and summary warnings

## Description

`ep.ml.calibrate` now defaults to Platt scaling because isotonic regression overfit the PhysioNet 2012 tuning set, `ep.ml.evaluate` and `ep.pl.subgroup_performance` keep the categorical order of `groupby`, and `ep.pp.summarize_measurements` returns NaN silently for windows without values. The changed calibration default changes results of code that relied on isotonic regression without passing `method`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `269c6bb07f8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.