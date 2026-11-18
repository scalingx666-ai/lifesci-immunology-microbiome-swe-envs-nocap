# Issue

**Title:** Remove obsolete benchmark module and unused files

## Description

The benchmark module has been superseded by our new benchmarking package at
 https://github.com/jakobnissen/VambBenchmarks.jl.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b782b7ae70a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.