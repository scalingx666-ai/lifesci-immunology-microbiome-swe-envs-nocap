# Issue

**Title:** Remove b.rate/b.rate.g2 deprecation guards

## Description

## Summary

- Removes the `b.rate` and `b.rate.g2` deprecation `stop()` guards from `param.dcm()`, `param.icm()`, and `param.net()`
- These parameters were renamed to `a.rate` / `a.rate.g2` back in v1.7.0; the custom error messages are no longer needed
- Users passing `b.rate` will now get standard R "unused argument" errors, which is appropriate for a parameter removed 7+ years ago

## Notes

The inconsistency originally reported in #989 (where `param.net()` used `stop()` but DCM/ICM used `message()`) was already resolved by #992, which standardized all three on `stop()`. This PR completes the cleanup by removing the guards entirely — no users should still be passing `b.rate` at this point.

## Test plan

- [x] `R CMD check` passes (no code references `b.rate` in tests or elsewhere)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c58928e2e334`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.