# Issue

**Title:** fix(vignette): don't require Suggests packages to build

## Description

## Why

`R CMD build` has been failing on `devel`:

```
Quitting from curatedMetagenomicData.Rmd:201-208 [unnamed-chunk-12]
Error in `library()`: ! there is no package called 'OmicsMLRepoR'
Error: Vignette re-building failed.
```

The chain behind it:

1. **`rols` was removed in Bioconductor 3.24.** It's in the 3.23 release (v3.8.2) and absent from the 3.24 package list.
2. **`OmicsMLRepoR` depends on `rols`**, so it now fails to install on all three Bioc devel builders — `ERROR: dependency 'rols' is not available` on nebbiolo2, lconway and taishan. A package that fails to install isn't propagated, so it can't be installed in the `bioconductor_docker:devel` container either. Tracked upstream at shbrief/OmicsMLRepoR#60, open since 2026-03-18.
3. **The vignette calls `library(OmicsMLRepoR)` unconditionally**, though it's only in `Suggests:`, and the whole Example Analysis section flows from `OmicsMLRepoR::getMetadata("cMD")`.

## What changes

The unconditional use is a bug on its own terms — `R CMD check` is allowed to run without `Suggests` installed, so a vignette must build without them regardless of what's happening upstream.

Availability is computed once, `eval` is set for the Example Analysis chunks, and reset before Type Conversion so Session Info still runs. When the packages are missing the analysis is still *shown*, just not executed, with a note naming what's absent — so the rendered vignette stays readable either way.

Verified locally with `OmicsMLRepoR` absent and `scater`/`vegan`/`lefser` present: `run_analysis = FALSE`, chunks render without executing.

## What this does not fix

`OmicsMLRepoR` still can't ship in Bioc 3.24 until it migrates off `rols`. This only stops that from taking `curatedMetagenomicData` down with it. Once OmicsMLRepoR is installable again the analysis evaluates as before, with no further change here.

## Test plan

- [ ] Vignette builds in the devel container with `OmicsMLRepoR` unavailable
- [ ] Example Analysis renders as code with the "not evaluated" note
- [ ] Session Info still executes (the reset works)
- [ ] `R CMD build` / `R CMD check` get past the vignette stage

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `116ac707bf8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.