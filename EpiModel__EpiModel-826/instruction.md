# Issue

**Title:** warnings on `get_partners`

## Description

this PR adds a MESSAGE on `get_cumulative_edgelist` when the `el_cuml` object do not exist yet.
If this message is printed at each time step, it means that `update_cumulative_edgelist` is not called. Otherwise, it appears the first time the `el_cuml`.

In addition, the `cumulative.edgelist` and `truncate.el.cuml` controls get default values in `netsim_validate_control` to reduce the overhead of checking for NULL each time we want to use them.

`control$cumulative.edgelist` is FALSE when calling `get_cumulative_edgelist`

New tests are added to validate these behaviors.

This PR probably should be merged after #765 to avoid merge conflicts

No changes were made to `get_partners` and `get_cumulative_edgelist_df` as they all call the `get_cumulative_edgelist` function and thus will trigger the messages / warnings as well

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a04f84843f04`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.