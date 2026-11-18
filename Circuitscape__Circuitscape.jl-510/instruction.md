# Issue

**Title:** CI: run each piece of work once

## Description

## Summary

Every push ran the core test suite five times, uploaded coverage five times, and ran doctests two or three times in the docs job. This PR keeps the same coverage of platforms, Julia versions, and extensions while running each piece of work once, and adds Pardiso testing on Windows.

- **Every Julia 1 job runs core plus the extensions its platform supports.** Ubuntu and Windows: core + Pardiso + GDAL. macOS: core + Accelerate + GDAL. Pardiso on Windows is new.
- **Drop the Julia 1 core-only jobs on Ubuntu and Windows.** They were strict subsets of the extension jobs above. The Julia `min` core job on Ubuntu stays.
- **Upload coverage from one job only.** The Ubuntu extension job reaches the most code. The other jobs run without coverage instrumentation, which also makes them faster.
- **Run doctests once.** Remove the explicit `doctest(Circuitscape)` step and pass `doctest = false` to the PDF `makedocs`, leaving the HTML `makedocs` as the single doctest pass.
- **Share the docs page list** between `make.jl` and `make_pdf.jl` via `docs/pages.jl`, so a new page is added in one place.

The test driver is unchanged.

## Test plan

- [x] `ci.yml` parses as YAML
- [x] `docs/make.jl` and `docs/make_pdf.jl` parse and load `docs/pages.jl` (8 pages)
- [ ] CI on this PR: Windows job installs Pardiso and runs the MKL suite, Ubuntu job uploads coverage, docs job builds PDF and HTML

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01R52oCkaGYuVJSPyHUMQrbn

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f59aea626535`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.