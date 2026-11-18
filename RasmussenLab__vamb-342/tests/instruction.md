# Issue

**Title:** Save VAEVAE latent as compressed npz

## Description

This could perhaps use a benchmark, just to be sure that removing bits from the latent space doesn't affect accuracy (though that is highly unlikely)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7bdc15cfe3c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.