# Issue

**Title:** feat(tests): enable --doctest-modules in pytest configuration

## Description

## Summary

Enable automatic doctest discovery for Python source modules by adding `--doctest-modules` to pytest and `src/sourmash` to `testpaths`.

## Changes

**`pyproject.toml`:**
- Add `--doctest-modules` to `[tool.pytest.ini_options] addopts`
- Add `"src/sourmash"` to `testpaths` so pytest collects doctests from source files

## Why

Issue #897 noted that doctests in source files (e.g., `sourmash/minhash.py`, `sourmash/lca/lca_utils.py`) were never executed in CI. The existing config only tested `doc/*.md` doctests via `--doctest-glob`. Adding `--doctest-modules` with `src/sourmash` in `testpaths` ensures source-level doctests are collected and run alongside unit tests.

## Notes

- The `-n4` parallel flag is compatible with `--doctest-modules` (xdist handles collection correctly)
- Source doctests that import `sourmash` require the compiled Rust extension, which is available in CI but not in bare Python environments

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `64e527f2384b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.