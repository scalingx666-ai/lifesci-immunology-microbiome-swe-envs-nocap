# Issue

**Title:** Some fixes prior to release

## Description

- Fixed full test skipping freyja (will add it again after updating the module in nf-core for the next release)
- Updated all versioning changes (some modules were updated but not indicated in chagelog)
- Updated changelog params (some params were added/removed  but not indicated in chagelog)
- Updated output documentation
- Fixed Nanopore multiQC summary variants metrics
- Fixed mosdepth amplicon that was broken for nanopore

Closed issues:
- #515 
- #516 

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)- [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58ea34b09d7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.