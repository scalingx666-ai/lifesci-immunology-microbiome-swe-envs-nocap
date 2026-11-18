# Issue

**Title:** Fix slow contig filtering by replacing list with set

## Description

This PR fixes a performance issue that caused **extreme slowdowns** when running Binette v1.2.0, particularly when using the `--proteins` flag or during CDS prediction.

In two places, contig filtering was performed using a **list** instead of a **set** — in the `filter_faa()` function (as detailed in #90) and when reading and filtering contigs before predicting CDS with Pyrodigal:

https://github.com/genotoul-bioinfo/Binette/blob/ddc4c855ec7e7fcc82165e4c3c4b04ef5c187bad/binette/main.py#L275-L282

Converting `contigs_in_bins` and `contigs_to_keep` to a **set** restores the expected performance.

### Related issues

* 
*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ca421f0392b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.