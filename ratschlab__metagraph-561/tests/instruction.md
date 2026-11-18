# Issue

**Title:** Optimization: don't serialize the inverse label mapping

## Description

I noticed that the label encoder alone for the large tara oceans assembly index takes 68 GB. (It has 318M labels.)
All labels there are stored twice (in the hash map and in the vector), however, we could store them once in an ordered set.

**Change**: Store labels in tsl::ordered_set that does both mappings.

Reduced the memory footprint and loading time of the label encoder by 2x (it can take dozens of gigabytes for millions of labels).

When loading old files with backward compatibility, it takes a little longer, but for <1M labels, it's negligible.
So, there is no need to necessarily update all generated annotations.

**Before / old format:**
```
	Elapsed (wall clock) time (h:mm:ss or m:ss): 2:07.23
	Maximum resident set size (kbytes): 68125144
```

**After / new format:**
```
	Elapsed (wall clock) time (h:mm:ss or m:ss): 0:53.46
	Maximum resident set size (kbytes): 33759768
```

**Backward compatibility -- loading the old format is a bit slower:**
```
	Elapsed (wall clock) time (h:mm:ss or m:ss): 2:22.73
	Maximum resident set size (kbytes): 45890504
```

<details>

**Before / old format:**
```
srv-metagraph@mex:~/metagraph/metagraph/build$ /usr/bin/time -v ./metagraph_DNA_master stats --mmap /scratch/nvme3/tara_assemblies/annotation.row_diff_sparse.annodbg
[2025-12-13 00:33:23.865] [info] Statistics for annotation '/scratch/nvme3/tara_assemblies/annotation.row_diff_sparse.annodbg'
=================== ANNOTATION STATS ===================
labels:  318205057
objects: 121058940696
density: 3.11012e-10
representation: row_diff_sparse
=================== DIFF ANNOTATION ====================
num anchors: 2037216349
underlying matrix: RowSparse
========================================================
	Command being timed: "./metagraph_DNA_master stats --mmap /scratch/nvme3/tara_assemblies/annotation.row_diff_sparse.annodbg"
	User time (seconds): 55.91
	System time (seconds): 69.94
	Percent of CPU this job got: 98%
	Elapsed (wall clock) time (h:mm:ss or m:ss): 2:07.23
	Average shared text size (kbytes): 0
	Average unshared data size (kbytes): 0
	Average stack size (kbytes): 0
	Average total size (kbytes): 0
	Maximum resident set size (kbytes): 68125144
	Average resident set size (kbytes): 0
	Major (requiring I/O) page faults: 0
	Minor (reclaiming a frame) page faults: 33371090
	Voluntary context switches: 22150
	Involuntary context switches: 401
	Swaps: 0
	File system inputs: 28067456
	File system outputs: 0
	Socket messages sent: 0
	Socket messages received: 0
	Signals delivered: 0
	Page size (bytes): 4096
	Exit status: 0
```

**After / new format:**
```
srv-metagraph@mex:~/metagraph/metagraph/build$ /usr/bin/time -v ./metagraph_DNA stats --mmap /scratch/nvme3/tara_assemblies/annotation.v4.row_diff_sparse.annodbg 
[2025-12-13 00:35:14.795] [info] Statistics for annotation '/scratch/nvme3/tara_assemblies/annotation.v4.row_diff_sparse.annodbg'
=================== ANNOTATION STATS ===================
labels:  318205057
objects: 121058940696
density: 3.11012e-10
representation: row_diff_sparse
=================== DIFF ANNOTATION ====================
num anchors: 2037216349
underlying matrix: RowSparse
========================================================
	Command being timed: "./metagraph_DNA stats --mmap /scratch/nvme3/tara_assemblies/annotation.v4.row_diff_sparse.annodbg"
	User time (seconds): 26.96
	System time (seconds): 25.56
	Percent of CPU this job got: 98%
	Elapsed (wall clock) time (h:mm:ss or m:ss): 0:53.46
	Average shared text size (kbytes): 0
	Average unshared data size (kbytes): 0
	Average stack size (kbytes): 0
	Average total size (kbytes): 0
	Maximum resident set size (kbytes): 33759768
	Average resident set size (kbytes): 0
	Major (requiring I/O) page faults: 36
	Minor (reclaiming a frame) page faults: 10122183
	Voluntary context switches: 14195
	Involuntary context switches: 191
	Swaps: 0
	File system inputs: 24988920
	File system outputs: 0
	Socket messages sent: 0
	Socket messages received: 0
	Signals delivered: 0
	Page size (bytes): 4096
	Exit status: 0
```

**Backward compatibility / loading old format now:**
```
srv-metagraph@mex:~/metagraph/metagraph/build$ /usr/bin/time -v ./metagraph_DNA stats --mmap /scratch/nvme3/tara_assemblies/annotation.row_diff_sparse.annodbg 
[2025-12-13 01:08:18.446] [info] Statistics for annotation '/scratch/nvme3/tara_assemblies/annotation.row_diff_sparse.annodbg'
=================== ANNOTATION STATS ===================
labels:  318205057
objects: 121058940696
density: 3.11012e-10
representation: row_diff_sparse
=================== DIFF ANNOTATION ====================
num anchors: 2037216349
underlying matrix: RowSparse
========================================================
	Command being timed: "./metagraph_DNA stats --mmap /scratch/nvme3/tara_assemblies/annotation.row_diff_sparse.annodbg"
	User time (seconds): 79.08
	System time (seconds): 63.35
	Percent of CPU this job got: 99%
	Elapsed (wall clock) time (h:mm:ss or m:ss): 2:22.73
	Average shared text size (kbytes): 0
	Average unshared data size (kbytes): 0
	Average stack size (kbytes): 0
	Average total size (kbytes): 0
	Maximum resident set size (kbytes): 45890504
	Average resident set size (kbytes): 0
	Major (requiring I/O) page faults: 39
	Minor (reclaiming a frame) page faults: 26216802
	Voluntary context switches: 3812
	Involuntary context switches: 522
	Swaps: 0
	File system inputs: 35222664
	File system outputs: 0
	Socket messages sent: 0
	Socket messages received: 0
	Signals delivered: 0
	Page size (bytes): 4096
	Exit status: 0
```
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc7cc94948c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.