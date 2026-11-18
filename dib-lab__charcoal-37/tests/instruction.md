# Issue

**Title:** redo rank matching to be more flexible than just `genus`

## Description

This PR adds a command line parameter, `--match-rank`, to `just_taxonomy.py`, that does decontamination at different ranks than genus.

the gather contamination check now asks if the lineage of the best gather result matches at that match rank. 
the first lca contamination check now asks if the lca of the hashval assignments for this contig is at or below match_rank, rather than explicitly genus/species/strain.
the second lca contamination check now asks if the taxonomy of the hashval assignment for this contig matches at that match rank.

we no longer require that the genome's classification is at genus level. if it is above that of match_rank, we pull match_rank back to it. So, e.g. if we assign Eukaryota to a genome, the match rank for detecting contamination becomes Eukaryota.

This PR also adds a few more test genomes in the default workflow, to exercise the various early exit options.

touches on #30

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f6179f7b031c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.