# Issue

**Title:** CI: distinct job names, drop Pardiso on macOS

## Description

.

Both test jobs used the same `name:` template, so master shows `Julia 1 - macOS-latest - push` and `Julia 1 - macos-latest - push` side by side, distinguishable only by case. That also means neither can be marked as a required status check.

Every job runs `Pkg.test()`, which always exercises **CG+AMG and CHOLMOD** and adds Accelerate or Pardiso only where they load. The job names now say so: `… - CG+AMG, CHOLMOD, Accelerate - …` on macOS and `… - CG+AMG, CHOLMOD, Pardiso - …` on Windows/Ubuntu.

MKL has no arm64 build, so the Pardiso job on `macos-latest` cannot load Pardiso — on master (`8c782de`) that job ran for 20+ minutes while the others finished in 3–5, and would only have repeated the macOS default-solver run. The Pardiso matrix is reduced to Windows and Ubuntu; macOS keeps its own job.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c782de05c1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.