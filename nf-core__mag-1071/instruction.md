# Issue

**Title:** perf: unflatten dastool_fasta2contig input

## Description

`DASTOOL_FASTATOCONTIG2BIN` was running once per bin, spawning a large number of jobs.
But this isn't necessary: `Fasta_to_Contig2Bin.sh` takes a directory (`-i`) and processes all FASTA files in it at once, producing the same contig2bin table.
This PR removes `.transpose()` so each binner's bins are passed as a single batch.

Notes:
- The fa extension is hardcoded instead of read per-file, since RENAME_PREDASTOOL guarantees every bin is renamed to .fa (it errors out otherwise). This matches how the TIARA subworkflow already calls the same module.
- Snapshot changes are limited to:
  - Fewer succeeded jobs, the direct benefit of this change.
  - `_DASTool_summary.tsv` / `_allBins.eval checksums`, only the source-filename column changes (now the per-binner contig2bin file rather than the per-bin one). All bin scores, sizes, and completeness values are identical.
  - No change to the refined bins (`.fa.gz`) or `_DASTool_contig2bin.tsv`.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bdae3e8943e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.