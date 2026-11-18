# Issue

**Title:** Add missing C++ standard library includes

## Description

## Summary
Added explicit `#include <cmath>` to `log_range_param.h` and `range_param.h`. These headers use symbols from `<cmath>` but relied on transitive includes, which can break with different compilers or standard library versions.

## Test plan
- [ ] Verify project builds successfully on CI

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67c8d6f3ac51`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.