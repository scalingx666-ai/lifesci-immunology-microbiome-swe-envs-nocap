# Issue

**Title:** get_posit_ids(): look up unique IDs by binary search

## Description

- Now: `get_posit_ids()` and `is_active_unique_ids()` call `match()` on the unique ID vector, which is slow on a large vector of consecutive integers: about 4 ms per call at 100k nodes.
- Goal: make the lookup cheap when a module asks for a few IDs. 0.2 ms for 300 IDs of 100k, with the same result.
- How: unique IDs are in increasing order, so a few of them are found with `findInterval()`, and larger sets are matched as doubles. Separately, `resim_nets()` counts the active nodes of each group with a logical sum, not `intersect()`.
- Review: technical only.

Part of the run-time work tracked in EpiModel/EpiModelHIV-p#427.

R's `match()` is slow on a large table of near-consecutive integers, which is what unique IDs and positional IDs are. Against a table of 100,000 such IDs one call takes 3.8 to 4.4 ms, and 0.5 to 0.7 ms when the same values are held as doubles (R 4.6.1 on an M5 Max; 5.6 to 6.6 against 1.2 to 1.4 ms on an M1 Max with R 4.5.3). `get_posit_ids()` and `is_active_unique_ids()` pay that on every call with integer IDs.

- `get_posit_ids()` now finds a few IDs (fewer than a sixteenth of the population) by binary search in the unique ID vector, which is in increasing order, and matches larger sets as doubles. If the IDs are not numeric or the vector is not sorted it calls `match()` as before. The result is what `match()` returns.
- `resim_nets()` counted the active nodes of each group in two-group models with `intersect()` on two ID vectors, about 11 ms per call at 100k nodes, twice per step. It now sums a logical vector.

Main (`c665760f`) against this branch, 100 steps, same seed, heap floor raised (`R_VSIZE=1G R_NSIZE=5M`), in milliseconds per step:

| Model | Machine | Full step | Module that looks IDs up |
|---|---|---|---|
| 100k EpiModelHIV | Laptop (M5 Max) | 186 to 180 | 9.4 to 2.8 |
| 100k EpiModelHIV | Xeon Gold 6526Y | 449 to 448 | 16.7 to 5.9 |
| 10k built-in SIS | Laptop | 19.1 to 19.2 | |

The module is the engine's rolling count of recent STI diagnoses, which converts a small set of IDs twice per step. Laptop figures are means of three replicates, the Xeon ones of two on a shared cluster node, where the 11 ms the module saves is inside the run-to-run spread of the full step. A built-in model that does not look IDs up does not change.

Accuracy, main against this branch under the same seed: on the 100k model `as.data.frame(sim)` and the complete final run state are identical, and so are eight seeded built-in models, one of them with two groups (the list is in #1145).

The new `test-posit-ids.R` compares the lookup with `match()` for integer and double tables, few and many IDs, departed, out-of-range, repeated, missing and non-integer IDs, an unsorted table and a table with `NA`. `R CMD check` with the long tests on: 5,011 expectations, no failures. Lint is clean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1afd71a8862e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.