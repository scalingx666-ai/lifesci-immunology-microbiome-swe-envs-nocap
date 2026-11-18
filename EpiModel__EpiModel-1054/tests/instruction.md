# Issue

**Title:** Fix param.net data.frame.params documentation

## Description

Finishes the remaining item on #1031.

`?param.net` documented the parameter table argument as `data.frame.parameters` from the time the section was added through v2.6.1. The constructor only ever accepted `data.frame.params`. Following the released docs produced no error: the data.frame fell through to `...` and was stored as a parameter literally named `data.frame.parameters`, so the table was never unpacked and the model ran misparameterized.

PR #1040 dropped the alias-handling code before merge but kept a docstring edit advertising `data.frame.parameters` as a deprecated alias, which was never true.

Changes:

- Remove the false alias claim from the roxygen and note that the old name was a documentation error; regenerate `man/param.net.Rd`.
- Reject `data.frame.parameters` with an error pointing to `data.frame.params`, matching how the other removed/renamed argument names are handled (#992). This turns the silent no-op into a clear message for anyone following the v2.6.1 docs.
- Regression test in `test-newmodules.R` covering both the rejected name and the correct one.

Per the #1040 review, `data.frame.parameters` is not being added as a working alias, since it was never an accepted name.

Full suite passes locally with `NOT_CRAN=true`: 3096 passing, 0 failures, 0 skips. Lintr clean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a265775abf14`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.