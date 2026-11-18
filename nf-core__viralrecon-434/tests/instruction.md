# Issue

**Title:** Enhanced BLAST results filtering

## Description

Fixed issue #378:
- Add taxonomic ID to BLAST output files
- Detailed in the documentation filters used to generate `.filter.blastn.txt`
- Added a header for raw .blastn.txt same as for filter.blastn.txt
- Added parameters for BLAST filtering

## PR checklist

- [X] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [X] Make sure your code lints (`nf-core lint`).
- [X] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [X] Output Documentation in `docs/output.md` is updated.
- [X] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8161eb9051d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.