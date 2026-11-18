# Issue

**Title:** Added kraken2 to nanopore workflow

## Description

Viralrecon Nanopore workflow does not run kraken2 tool (while Illumina workflow does).

- Added kraken2 to nanopore workflow.
- Fixed single-end/paired-end reads detection in kraken module.
- Added kraken2_db to prepare_genomes.
- Updated test.config files for nanopore testing.

 

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)- [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `295a1d553d39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.