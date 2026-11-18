# Issue

**Title:** adding ncbi fallback restoration and mapfile

## Description

- Adding NCBI taxon lookup fallback (requires internet access) if a local assembly doesnt match the refseq file.
- Adding optional genbank pull of genomes as well as being able to use a local gb summary file (use `--enable_genbank`). If locally pulled use: `assembly_summary_genbank`
- adding a custom ncbi mapfile `custom_accession_map`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac46260aa062`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.