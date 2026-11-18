# Issue

**Title:** Generalize structure protein key

## Description

Part of the Colabfold integration (#2754), step 5 following #2755 #2759 #2760 #2763.
Here is a very technical PR. All about plumbing. The idea was to change how the protein id were defined and used to allow for new input type (like a pangenome, maybe just a fasta, etc).

Before this PR, the codes was referring to all protein with `corresponding_gene_caller_id` which was the gene caller id hard-linked to a single contigs database.

What is in this PR:
- a new protein id replacing the gene caller id. + a new proteins table which records input type (contigs.db for now), genome name, gene caller id, gene cluster id, source key, has structure. And self gained an 'input type' entry. Kept 'contigs_db_hash' for now.
- New class StructureInputSource so that StructureSuperclass delegate input validation and sequence fetching to a source object. ContigsDBSource is the only implementation for now, but there is a space for PangenomeSource.
- A migration from v3 to v4 for the structure db.

Important note:
For a contigs db source, the `protein_id` == `gene_caller_id`. All downstream code like variability overlay is identical and unchanged.

Tests are on going, and I'll report quickly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4fb97a81201c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.