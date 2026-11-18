# Issue

**Title:** Split the netsim_dat accessor help page by group

## Description

.

The accessors in `R/net.fn.accessor.R` shared one help page, so `?get_attr`, `?set_epi`, and `?set_param` all landed on the same long page. This splits them by the part of `dat` they act on:

- `?get_attr`: nodal attributes, including `append_core_attr()` and `get_core_attributes()`
- `?get_epi`: epidemic outputs
- `?get_param`: parameters, controls, and initial conditions

`?net-accessor` stays as an overview listing the three pages, so the existing `help("net-accessor")` references in vignettes, NEWS, and downstream packages still work. Each page inherits the Intended Usage and Mutability sections from it with `@inheritSection`, so the #1024 guidance is on every page but written once.

Each page now documents only its own arguments. For example, `?get_epi` says that `set_epi()` is the only `set_` function taking `at`, which must be named, and `?get_param` says its `set_` functions take neither nodes nor a time step. `@order` puts the primary function first in each usage block.

The old attribute example appended values for 10 new nodes without calling `append_core_attr()` first, which broke the page's own One Value Per Node rule. The new example adds the nodes first.

This is based on `dev` because #1007 rewrites the same doc block for the new `set_epi()` signature, and `?get_epi` documents that signature.

Also documents `ylim` in `plot.netsim()` rather than inheriting it from `graphics::plot`. The base R wording differs across R versions, so regenerating the docs flipped the `ylim` entry in five plot Rd files depending on who ran roxygen (it flipped back in #1087). The other plot methods inherit it from `plot.netsim()`.

`R CMD check --as-cran` passes with one NOTE (no prebuilt vignette index, from building without vignettes). `pkgdown::check_pkgdown()` and lintr are clean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4fd130f70389`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.