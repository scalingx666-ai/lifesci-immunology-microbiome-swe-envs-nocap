# Issue

**Title:** Fix plot.dcm ignoring custom legend names when nruns=1 and lcomp>1

## Description

The else branch (when leg.name is provided) had the lcomp>1 check at the same level as lcomp==1, causing it to fire even when nruns==1. This overwrote user-provided legend names with defaults and emitted a spurious warning. Restructure the conditionals so the warning only triggers when both nruns>1 and lcomp>1, and custom leg.name is used directly when nruns==1.



https://claude.ai/code/session_01M3of9Me9mL4EQDbTFgbpHL

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d221983fb45`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.