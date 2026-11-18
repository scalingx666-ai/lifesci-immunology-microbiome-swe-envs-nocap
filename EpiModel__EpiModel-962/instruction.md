# Issue

**Title:** Future

## Description

Use `future` instead of `foreach` to handle parallelization.

The [`future`](https://future.futureverse.org) package makes parallelization easy and flexible. Here it allows us to keep the simplicity of `ncores == N` to automatically create `multisession` (PSOCK) backend that are ubiquitous and safe backend for `netsim` and `netdx`. For advanced users, the `future.use.plan` flag will use the users chosen setup. This ranges from `multicore` (forks on Unix-like systems) all the way to complex systems like `mirai` or `batchtools`. 

As an added benefit, the `future.seed` flag also ensures a safe handling of multicore Random Number Generation. That was possibly an issue with the `%dopar%` implementation where we possibly should have used the `doRNG` packages.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `abf650559deb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.