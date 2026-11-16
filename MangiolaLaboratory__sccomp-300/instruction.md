# Issue

**Title:** Fix master rworkflows jobs that fail at setup

## Description

## Summary
- The three failing master checks are the rworkflows jobs (ubuntu, macOS, and Windows). Each dies during "Set up job" because `neurogenomics/rworkflows@master` still downloads `catchpoint/workflow-telemetry-action`, and that repository now returns 404.
- Turning telemetry off does not help: GitHub resolves every composite `uses:` before it evaluates `if`.
- This vendors `neurogenomics/rworkflows@6aaf493` (v1.0.12) under `.github/actions/rworkflows` and drops the telemetry step, then points the workflow at that local action.

## Test plan
- [ ] Confirm the three rworkflows jobs get past "Set up job" on this pull request
- [ ] Confirm `workflow_with_cmdstanr` is unchanged and still not part of this failure

Made with [Cursor](https://cursor.com)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e1fc106a1c81`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.