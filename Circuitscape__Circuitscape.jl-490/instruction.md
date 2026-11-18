# Issue

**Title:** CI: run Pkg.test with coverage=true

## Description

Codecov has reported **0%** on every commit since 2026-04-07; the last real figure was 83.3% (`2110ffa`).

#463 replaced `julia-actions/julia-runtest` with an inline `Pkg.test()` so `AppleAccelerate`/`Pardiso` could be `Pkg.add`ed first. `Pkg.test()` defaults to `coverage=false`, so no `.cov` files were written; `julia-processcoverage` then uploaded an empty `lcov.info` and Codecov recorded it as 0%. Uploads have been succeeding the whole time, which is why nothing looked broken from the CI side.

Fix: `Pkg.test(coverage=true)` in both jobs. Nothing else changes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d57c774e946`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.