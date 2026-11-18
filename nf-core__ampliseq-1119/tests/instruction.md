# Issue

**Title:** Lower DADA2 addSpecies memory: smaller n, chunk size per reference database

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] `CHANGELOG.md` is updated.
## Description

DADA2 `addSpecies` with SILVA 144 needs more memory than the pipeline can give it on `test_full`.
A 10,000-ASV chunk was killed at the 50 GB first-attempt limit and again at 96 GB.

`assignSpecies()` in DADA2 keeps one yes/no vector per query ASV, with one entry per reference sequence, until the last batch is done.
SILVA 144 has 1,466,213 species reference sequences, so that is about 5.9 MB per ASV and 59 GB for a 10,000-ASV chunk.
This is fixed on the DADA2 side in benjjneb/dada2#2221, which makes the memory independent of the number of queries.

Until that is released, the chunk size is lowered for SILVA 144.

### Changes

- A database can set `chunksize` in `conf/ref_databases.config`; it is 2000 for SILVA 144 (`silva` and `silva=144`).
  The ASV fasta is split once per distinct chunk size, so other databases keep 10000.
- `--dada_assign_chunksize` has no default any more; the value order is the parameter, the database's `chunksize`, then 10000.

`n` in `modules.config` is unchanged.
Lowering it to 100 saved at most 7 GB for a 2000-ASV chunk and made `addSpecies` about 50% slower.

### Measured (SILVA 144, 2000 ASVs of mostly 252 to 254 nt, DADA2 1.40.0)

A 2000-ASV chunk needs about 26 GB at `n = 1e5`, below the 50 GB limit.

### Checked

- `prek`, `nf-core pipelines lint` and `nextflow lint .` (26.04.0, 26.04.6, 26.04.7).
- `nf-test` for `default` and `multidb` (both pass, snapshots unchanged).
- No new test: no CI profile uses SILVA 144, so the per-database chunk size is not exercised there.
  The chunk logic was run in a stand-alone workflow with different sizes per database and with the parameter set.

Analysis and changes prepared with Claude Code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd4cfe76a1b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.