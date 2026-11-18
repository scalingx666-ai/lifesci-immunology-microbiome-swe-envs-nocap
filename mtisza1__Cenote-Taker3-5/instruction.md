# Issue

**Title:** Update3 (v3.3.0 updates)

## Description

redoing read coverage parsing from samtools coverage: `make_sequin_cmts.py`

Adding read coverage to summary table. Adding virus gcode to virus summary table: `virus_summary.py`

Fixing minor error/warning when trying to create a directory that exists: `assess_virus_genes1.py`

adding sequencing tech argument `--seqtech`

Added/integrated a new taxonomy database "hallmark". This database is compiled from: 1) genbank nr clustered -> extracting virus proteins with taxonomical labels for genus, family, and class -> filtering to seqs with CT3 hallmark gene hits -> reclustering at 90% AAI with `cd-hit` and 2) refseq virus -> filtering to seqs with CT3 hallmark gene hits

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58930a2c9686`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.