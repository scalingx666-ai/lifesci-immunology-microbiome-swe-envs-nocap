# Issue

**Title:** Move computation

## Description

Move all computation into models.py SimSirModel.

Most properties of Parameters have moved to the SimSirModel.

Replace vectors with raw df from sim_sir_df.

Use column names from sim_sir_df.

Use column names from dispositions dictionary in a way that allows dispositions to be extended beyond 'hospitalized', 'icu', 'ventilated' in model.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `39185aa11d95`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.