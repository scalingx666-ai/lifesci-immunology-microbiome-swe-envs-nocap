# Issue

**Title:** Update/new-gtdb-tk

## Description

`HiFi-MAG-Pipeline`:
- Updated  to require GTDB-Tk V2.0.0+, and ensured compatibility with GTDB 07-RS207 (release 207).
- Set default max contigs per MAG to `20`.
- Added image showing "circular-aware binning" to docs.
- Updated docs.

`Taxonomic-Functional-Profiling-Protein`:
- New default behavior is to output two RMA files per sample. The `{sample}_filtered.protein.{mode}.rma` results from the optimal MEGAN-LR filter for precision/recall balance, whereas the `{sample}_unfiltered.protein.{mode}.rma` file has no filtering (e.g., any read assigned to any taxon is reported). The filtering parameter for `{sample}_filtered.protein.{mode}.rma` is still be controlled with the `sam2rma: minSupportPercent` argument in the `config.yaml` file; the default is `0.01`.
- Updated docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `678ae040b7d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.