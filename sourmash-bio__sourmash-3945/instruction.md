# Issue

**Title:** Feat: Re-enable `repair` and return errors more widely

## Description

Fix #3862 

- Re-enable `repair` functionality, so we can recover from errors due to dataset list corruption (the `RoaringBitmap unknown cookie` error)
- Bump core to `0.23.0`
- `counter_for_query`,`prepare_gather_counters`,`load_hashes` all return `Result<...>` now, so we can capture errors.
- `stats_for_cf` now reports `failed_keys`  if doing a full check, so we can capture errors due to dataset list corruption
- Bump codecov-action, install codecov-cli from pypi
- Only reuse shared lib for rocksdb in Linux, macOS has issues finding it from the pixi env

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9c998c1fc08`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.