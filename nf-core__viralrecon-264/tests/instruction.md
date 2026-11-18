# Issue

**Title:** Fix variants in consensus

## Description

Now variants in vcf files are going to be filtered with bcftools filter to select variants higher than 0.75 AF before the consensus genome generation. Also, for bcftools it was needed to split multiallelic variants in diferent lines to make bcftools filter work.

Finally a new module to rename consensus fasta header has been aded, which will work both for multifasta reference or single fasta reference.

## PR checklist

- [X] This comment contains a description of changes (with reason).
- [X] If you've fixed a bug or added code that should be tested, add tests!
    - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
    - [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eed75c3df125`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.