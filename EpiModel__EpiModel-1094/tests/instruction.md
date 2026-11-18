# Issue

**Title:** Table only the attributes nwupdate.net() fills in

## Description

`nwupdate.net()` called `get_attr_prop()` on every time step with arrivals, and that tables every nodal attribute, including `unique_id` and any continuous attribute such as age, which have about one table entry per node. `auto_update_attr()` only ever fills in the attributes the arrivals module left short, so most of those tables were thrown away, and in a model whose arrivals module sets every attribute all of them were.

This finds the short attributes first, tables only those, and skips the tables entirely when there are none. `get_attr_prop()` gets an `attrs` argument for the restriction. `auto_update_attr()` now looks up each attribute's time 1 table by name rather than by position, since the positions in a restricted table no longer line up with `t1.tab`.

In the GlobalMix India model (117,810 nodes, four layers, arrivals every step, every attribute set by the arrivals module), seeded 60-step rural runs went from 48.5 s to 26.9 s. Output is unchanged: `epi` is identical to main for those runs, and identical to a custom nwupdate module with no fill-in at all for seeded 365-day rural and urban runs.

New tests in `test-netattr.R` cover the skip, the restriction, and the lookup by name (that one fails if the lookup goes back to position). `R CMD check --as-cran` passes apart from the version-number warning, since DESCRIPTION is still 2.6.2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af378215aa34`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.