# Issue

**Title:** CI: install treelayout and tidytree from CRAN before dependencies (temporary)

## Description

Fixes the CI failure seen in #882 without adding GitHub dependencies to `DESCRIPTION` (replaces the closed #937).

## Problem
- **ggtree needs a newer CRAN package:** ggtree in Bioconductor devel (4.3.2) imports **treelayout**, a new CRAN package first published on 2026-11-11.
- **The CI's CRAN snapshot is older:** the `bioconductor:devel` container used in CI installs CRAN packages from a snapshot dated **2026-10-28** (`p3m.dev/cran/__linux__/noble/2026-10-28`), which does not contain treelayout.
- **Result:** whenever the CI reinstalls dependencies, ggtree fails to install and R CMD check stops with "Package suggested but not available: 'ggtree'".

## Fix
- **New workflow step:** a temporary step in `.github/workflows/rworkflows.yml` installs **treelayout** and **tidytree** from CRAN (`cloud.r-project.org`) before the `rworkflows` step, so the ggtree upgrade finds them. ggtree 4.3.2 also needs tidytree >= 0.4.9 (for `offspring_bulk`), while the snapshot has 0.4.8. `DESCRIPTION` gets no new dependencies or `Remotes:`.
- **Version bump to 1.1.12:** this makes the CI reinstall the dependencies, so this PR's own check actually tests the fix. With an unchanged version, the cached library is reused and nothing is reinstalled. The same bump is already in #882's branch, so the two merge cleanly.

- **Cache version `cache-v1` -> `cache-v2`:** the R library is rebuilt from scratch, so the fix is tested with a fresh install. In the first run, the new ggtree still failed to install (because of tidytree), and the check passed only because an older ggtree was restored from the cache.

The step can be removed once the container's CRAN snapshot includes both packages.

After this is merged, merge `devel` into #882's branch to rerun its checks.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b907b4ac55c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.