# Issue

**Title:** map sequences to graph with dynamic omp schedule for better performance

## Description

Use dynamic scheduling to fix the imbalanced load on the threads


### **tara_assemblies:**

```
/usr/bin/time -v ./metagraph query /data/random_stud/queries/100_studies_50k_short.fq --mmap -p 40 -v -i graph_small.indexed.dbg -a annotation.v4.row_diff_sparse.annodbg -v --batch-size 10000000000 --query-mode matches > /dev/null
```

```
# Before:
[trace] Contigs mapped to the full graph (found 1721062 / 568137958 k-mers) in 401.965816809 sec
# After:
[trace] Contigs mapped to the full graph (found 1721062 / 568137958 k-mers) in 251.316558261 sec
```

### **all_sra/data/metagenome/1315:**

```
# Before:
[trace] Contigs mapped to the full graph (found 18968780 / 532119762 k-mers) in 573.547590432 sec
# After:
[trace] Contigs mapped to the full graph (found 18968780 / 532119762 k-mers) in 381.756807251 sec
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c6094a94b0b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.