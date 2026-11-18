# Issue

**Title:** Singlem update

## Description

SingleM hasn't worked for a while, fixing now it has been released on conda recently (0.14.0).

To do:
- [x] Update singlem commands
- [x] Fix appraise plot bug - @AroneyS ?
- [x] Require SINGLEM_METAPACKAGE_PATH to be defined a la GTDBTK data env variable
- [x] Update integration tests to check singlem is working correctly there
- [x] Merge this into dev, not main

Current plotting bug:
```
$ SINGLEM_METAPACKAGE_PATH=/work/microbiome/db/singlem/S3.2.0.GTDB_r214.metapackage_20230428.smpkg.zb aviary recover -o out -1 test/data/wgsim.1.fq.gz -2 test/data/wgsim.2.fq.gz -n 32 -t 32
...

$ tail out/data/singlem_out/singlem_log.txt -n20
...
10/02/2023 08:39:07 AM INFO: Generating plot for marker: S3.52.rpsC_bact
[2023-10-01T22:39:07Z INFO  bird_tool_utils::clap_utils] Smafa version 0.6.1
[2023-10-01T22:39:07Z INFO  smafa::cluster] Clustering ..
[2023-10-01T22:39:07Z INFO  smafa::cluster] Clustering complete, took 0 seconds. Clustered 9 sequences into 2 clusters.
Traceback (most recent call last):
  File "/mnt/hpccs01/work/microbiome/conda/7b0823f7cd81a673d44f7e4adbc747aa_/bin/singlem", line 1021, in <module>
    app.plot(
  File "/mnt/hpccs01/work/microbiome/conda/7b0823f7cd81a673d44f7e4adbc747aa_/lib/python3.10/site-packages/singlem/appraisal_result.py", line 80, in plot
    self._plot_gene(
  File "/mnt/hpccs01/work/microbiome/conda/7b0823f7cd81a673d44f7e4adbc747aa_/lib/python3.10/site-packages/singlem/appraisal_result.py", line 269, in _plot_gene
    self._plot_scale(axis, max_total_count)
  File "/mnt/hpccs01/work/microbiome/conda/7b0823f7cd81a673d44f7e4adbc747aa_/lib/python3.10/site-packages/singlem/appraisal_result.py", line 352, in _plot_scale
    overlap = (ylim[1]-ylim[0]-sum(sides))/(len(sides)-1)
ZeroDivisionError: float division by zero
```

I think there is 2 things here - it shouldn't error, and should generate the plot. Also, it shouldn't choose a domain-specific gene to plot, it should use one that targets both Archaea and Bacteria.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `51516da4853d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.