# Issue

**Title:** Strand-bias and codon fixing for ivar

## Description

This PR is related to #247 
-  strand-bias filtering option is added to `ivar_variants_to_vcf.py` following instructions [here](https://gatk.broadinstitute.org/hc/en-us/articles/360035532152-Fisher-s-Exact-Test)
- Consecutive variants in ivar tsv output file are collapsed if they belong to the same codon, while parsing tsv file to vcf. 

## PR checklist

- [ X ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
    - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
    - [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [X] Make sure your code lints (`nf-core lint`).
- [X] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08e0aaaaa809`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.