# Issue

**Title:** Update semibin to v1.3

## Description

This updates SemiBin to v1.3 and switches to self-training by default. This closes 

SemiBin v0.5 runtime of the `train` step on HPC node with 20 CPU:

|s                |hours:minutes:seconds|max_rss                                                            |max_vms|max_uss|max_pss|io_in |io_out|mean_load|cpu_time|
|-----------------|-----|-------------------------------------------------------------------|-------|-------|-------|------|------|---------|--------|
|4246.2376        |1:10:46|1657.34                                                            |4792.95|1651.03|1651.46|497.45|0.09  |906.11   |37477.90|

The output of the SemiBin v1.3 benchmark of the new `train_self` step on HPC node with 20 CPU:

|s                |hours:minutes:seconds|max_rss                                                            |max_vms|max_uss|max_pss|io_in |io_out|mean_load|cpu_time|
|-----------------|-----|-------------------------------------------------------------------|-------|-------|-------|------|------|---------|--------|
|3972.1639        |1:06:12|2861.91                                                            |8327.03|2857.93|2858.25|236.23|0.08  |1963.73  |78005.33|

v1.3 skips the GTDB download (~1 hour) and MMSeqs2 clustering (~20min per sample for `predict_taxonomy`) for speed gains. I have not fully evaluated the gains in terms of number of bins, completeness of bins etc. for lack of a good baseline.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42c4cbd51514`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.