# Issue

**Title:** Fix broken vignette image links in introduction.Rmd

## Description

Images in `vignettes/introduction.Rmd` were broken when viewed as rendered articles/vignettes on the pkgdown site and Bioconductor.

## Root cause
- The vignette referenced images via `../inst/logo-01.png` and `../inst/cartoon_methods.png`.
- This relative path only resolves when browsing the raw source tree. Once the vignette is rendered as a standalone article (pkgdown site, Bioconductor landing page), `inst/` is no longer reachable relative to the rendered output location, so the images 404.

## Changes
- Copied `logo-01.png` and `cartoon_methods.png` from `inst/` into `vignettes/`, so they're bundled alongside the rendered vignette output. Originals left in `inst/` since `README.md` still references them from the repo root, where that path works fine on GitHub.
- Updated `vignettes/introduction.Rmd` to reference the images with local relative paths instead of reaching into `inst/`:

```diff
- # <img src="../inst/logo-01.png" height="139px" width="120px"/>
+ # <img src="logo-01.png" height="139px" width="120px"/>
  ...
- <img src="../inst/cartoon_methods.png" width="100%"/>
+ <img src="cartoon_methods.png" width="100%"/>
```
- Confirmed no other image references in `vignettes/introduction.Rmd` or `vignettes/splines.Rmd` use this broken pattern (remaining ones are absolute URLs).

<!-- START COPILOT CODING AGENT SUFFIX -->

-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49e6f3af4d0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.