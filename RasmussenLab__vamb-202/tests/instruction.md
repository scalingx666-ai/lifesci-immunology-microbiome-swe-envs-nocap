# Issue

**Title:** Fix bugs in scripts

## Description

Deleted `cmd_benchmarks.py` because it's wildly outdated. Use https://github.com/jakobnissen/VambBenchmarks.jl instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc07d4c498f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.