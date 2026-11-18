# Issue

**Title:** Simplfy $BEGINDATA and $ENDDATA logic

## Description

These fields can be padded with zeros wide enough to fit ~1TB of data. This saves 158 lines of code+tests and improves perf by avoiding calling `_build_text` twice.

FlowKit tests pass: https://github.com/primitybio/FlowIO/actions/runs/3130094612

---

I have one or two more PRs left to propose.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e8f0389f055`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.