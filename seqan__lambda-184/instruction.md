# Issue

**Title:** Iterative search

## Description

~~THIS IS A DRAFT~~

We now have the following extra command line arguments:

```
--search0 [bool] whether to perform the pre-search/iterative-search
--seed-length0
--seed-offset0
--seed-delta0
```

Where the respective seeding-options apply to the pre-search step. By default, everything is deactivated. When activated, length and offset are the same as before, but delta is set to 0. This type of search should never reduce the #queries with one hit, but improves performance by 10-20%.

I have had promising results with the following configs
```
--search0 1 --seed-length0 9 --seed-offset0 9 --seed-delta0 0 --seed-length 11 --seed-offset 11 // basically -1 pre and +1 post
--search0 1 --seed-length0 9 --seed-offset0 3 --seed-delta0 0 --seed-length 12 --seed-offset 4 // longer seed but more offset
--search0 1 --seed-length0 9 --seed-offset0 3 --seed-delta0 0 --seed-length 11 --seed-offset 8 // "best" sensitivity
```
These yield speed-ups of up to 30-70%, but none of these reach previous sensitivity. Results also differ a lot between datasets. For example, the last config only costs 1% sensitivity on the 125 transcriptome dataset, it costs ~4% on the 251 WGS dataset.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c00a16f5fcd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.