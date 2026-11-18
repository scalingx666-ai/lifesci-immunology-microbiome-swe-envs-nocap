# Issue

**Title:** Merge cumulative edgelist spells as an interval union

## Description

.

`dedup_cumulative_edgelist()` used `max()` and `min()` inside a grouped `mutate()`, which take the group-wide value, and compared each row only to the one before it. So it invented spells across gaps, left overlaps, and closed ongoing spells, and `get_forward_reachable()` / `get_backward_reachable()` could then report false paths.

It's now the per-pair interval union suggested in the issue: treat a `stop` of `NA` as `Inf`, sort by `start`, start a new spell when a row starts after every earlier row of the pair has stopped, and take `min(start)` and `max(stop)` per spell. A few details:

- Spells that touch at a step (`[1, 3]` and `[3, 6]`) merge; adjacent ones (`[1, 3]` and `[4, 6]`) stay separate, as before.
- Columns other than `start` and `stop` are part of the key, so the same pair on two layers of a `network` column is not merged. The old code grouped on `head` and `tail` only but carried other columns along.
- Column types and the input class (e.g. `cumulative_edgelist`) are kept, and the output is sorted by pair and `start`.

The help page now says how spells are merged, and the `\dontrun` example is replaced with one that runs. The vignette section was already accurate once the function works, so I left it alone.

New test in `test-cumulative_edgelist.R` covers a duplicated two-spell pair, overlapping/nested/touching/adjacent spells, ongoing spells, separate pairs and layers, and types and class. It fails on main.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fda1a55248ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.