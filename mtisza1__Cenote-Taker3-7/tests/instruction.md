# Issue

**Title:** Update4, to v3.3.1

## Description

Changes from `v3.3.0`:

1. Added argument `--max_dtr_assess`. Users can enter a maximum contig length to evaluate DTRs (default 1000000). Practically, long DTR-containing contigs are probably bacterial chromosomes and should be evaluated for prophages and pruned. Since DTR-containing contigs do not get pruned, this was preventing some bacterial chromosome assemblies from getting pruning treatment. 
2. Fixed `hhpred_to_table.py` gene_name variable parsing, which previously incorrectly used .strip() function.
3. Fixed location of `MMSEQS_outdir` in `get_ct3_dbs` command to avoid error.
4. For read-mapping, `--seqtech` now effects `minimap2` settings

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20df19d969d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.