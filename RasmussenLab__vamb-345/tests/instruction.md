# Issue

**Title:** Do not ingore errors caught by Loguru

## Description

In 62baa358, I added `@logger.catch` to `run` in order for Loguru to catch and log any errors emitted by Vamb.
However, I did not notice that this will cause any caught errors to exit Vamb with a return code of zero.
This broke CI and undoubtedly will break snakemake pipelines relying on Vamb.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7bdc15cfe3c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.