# Issue

**Title:** Add intermediate megahit_core_popcnt for CPUs that have ABM but not BMI2

## Description

Our compute cluster is based on Intel(R) Xeon(R) CPU E5-2670 v2 CPUs which provide the
ABM (i.e. POPCNT, LZCNT) extensions but neither BMI nor BMI2; this PR adds an additional
megahit core binary to address these scenarios.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1af4f0597cb0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.