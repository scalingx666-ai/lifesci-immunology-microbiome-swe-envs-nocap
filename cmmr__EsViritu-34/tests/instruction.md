# Issue

**Title:** to v1.2.0

## Description

Features:
- Adding `esv_create_taxonomy` and `esv_combine_tax` for custom DB creation. See instructions on the [docs](https://esviritu.readthedocs.io/en/latest/)
- support for long reads - ONT or PacBio. see `--minimap2-preset`

Fix:
- Appropriate logic for "denominator" read count for all preprocessing possibilities
- replacing `curl` with `url` in `google_fonts()` check in R script for report generation
- pi calculation error

Performance Improvements:
- parallelize contigs stats with `_calculate_contig_stats_from_bam()`, `bam_coverage_windows()` #31 
- improve clustering logic `cluster_assemblies_by_read_sharing()`
- samtools sort threading

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0ae41212cc1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.