# Issue

**Title:** Optimized select_support_mcl in sdsl-lite for faster loading with mmap

## Description

This saves ~5 sec for loading ~30GB indexes. Now they load practically instantly.

Before:
```
	User time (seconds): 1.16
	System time (seconds): 4.00
	Percent of CPU this job got: 99%
	Elapsed (wall clock) time (h:mm:ss or m:ss): 0:05.17
	Maximum resident set size (kbytes): 257280
```

After:
```
	User time (seconds): 0.16
	System time (seconds): 0.33
	Percent of CPU this job got: 76%
	Elapsed (wall clock) time (h:mm:ss or m:ss): 0:00.64
	Maximum resident set size (kbytes): 584448
```

(for command: `DIR=$(echo /scratch/0008); /usr/bin/time -v ./metagraph query -a $DIR/annotation.clean.row_diff_brwt.annodbg -i $DIR/graph.primary.small.dbg /scratch/query.fa --mmap -v`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a3de5a5a644`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.