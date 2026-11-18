# Issue

**Title:** Speed and memory optimization of `extract_map_reads.py`

## Description

One of the long awaited improvement is finally there, using PySam and cleverer set operations, the host_removal step is now much much leaner on memory and runtime

For example, for a 5.1 GB bam file (~95 million reads), and its associated forward (5.2GB) and reverse (5.4 GB) gzip compressed fastq files, it took only 19m21s and 90 MB of memory. 

The CLI stays the same

 

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [ ] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8271378a3d43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.