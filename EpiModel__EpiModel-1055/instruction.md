# Issue

**Title:** Release metadata, package overview rewrite, and dead NEWS links for v2.6.2

## Description

Covers items 1, 2, and 4 of the v2.6.2 release review.

**DESCRIPTION Date.** Bumped to 2026-07-29 to clear the "Date field is over a month old" NOTE. Worth re-bumping if submission slips more than a month out.

**Package overview rewrite.** `?EpiModel-package` still described the v2.4-era package. It claimed controls accept new modules for ICMs (removed in v2.6.1), said nothing about the extension API or the accessor functions that are now the main research interface, and pointed at no learning resources.

It also opened with a hand-maintained table of version, date, license, and LazyLoad. That table duplicated `DESCRIPTION`, was stale at 2.6.1/2026-05-12, listed two fields `DESCRIPTION` does not have, and sat in the `\description{}` block, so the actual package description never rendered on the help page. Dropping it lets roxygen fill `\description{}` from `DESCRIPTION`.

The new text covers the three model classes and what distinguishes them, the setup and simulation functions for each, the network-only extension API and its accessors, working with simulation output, and pointers to the vignettes, the NME course materials, and the Gallery. All 39 cross-references resolve.

Also splits the long `@importFrom stats` line. `.lintr` pinned a `line_length_linter` exclusion for this file to line 136, which the rewrite would have silently invalidated; the split removes the need for the exclusion entirely. `NAMESPACE` is unchanged.

**Dead NEWS links.** The multinets and observed-network-data examples were removed from the Gallery, so both links in the 2.4.0 entries 404'd. They now point at the corresponding NME chapters on multi-layer networks and epidemics over observed networks.

**Build ignore.** Added `CRAN-*.md` and `cran-comments.md` to `.Rbuildignore` so release-prep docs in the repo root do not trigger the "Non-standard file/directory found at top level" NOTE.

Checks:

- `R CMD check --as-cran --no-manual`: Status OK, 0 errors, 0 warnings, 0 notes.
- `NOT_CRAN=true R CMD check --no-manual`: Status OK, 3100 passing, 0 failures, 0 skips, 7 expected tergmLite warnings.
- `urlchecker::url_check()`: all 30 URLs correct.
- `lintr::lint_package()`: 0 findings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `daf860f68706`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.