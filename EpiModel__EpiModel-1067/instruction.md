# Issue

**Title:** Fix nodal attribute length invariant in set_attr() and append_attr()

## Description

.

Three fixes, all in the nodal attribute accessors.

`set_attr()` with `posit_ids` on an attribute that does not exist yet snapshotted the attribute list, created the attribute, then wrote into the stale snapshot. Assigning into `NULL` gave a vector as long as the highest selected position, so the length depended on which nodes were picked: length 2 for `posit_ids = c(1, 2)`, length 7 for `c(4, 7)`, in a 10 node model.

`append_attr()` on an attribute that does not exist yet started from `NULL`, so the result held only the appended values. An arrivals module that creates a custom attribute the first time any arrival occurs left that attribute covering the new nodes alone. Both now fill the nodes they do not write to with `NA`.

`check_attr_lengths()` errored on its first line for every input (`$` on the atomic vector `vapply` returns) and reported attribute positions rather than lengths. It is fixed and wired in: `netsim()` calls it at the end of each time step, after the modules and trackers. That is the one behavior change worth watching, since a model that ends a step with a wrong-length nodal attribute now gets a hard error naming the attribute instead of continuing. Temporary inconsistencies within a step are still fine, since the check runs once per step rather than per module. The full local suite is clean, including `test-net-long.R`, so no built-in path trips it.

Tests: creation through `posit_ids`, `NA` for unselected and pre-existing nodes, type preservation through the padding, `append_core_attr()` from an empty attribute list, and `check_attr_lengths()` on both a good and a corrupted object. Also a `netsim()` regression test with an arrivals module that first appends a custom attribute mid-simulation, asserting every attribute covers every node at the end.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `125d50444034`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.