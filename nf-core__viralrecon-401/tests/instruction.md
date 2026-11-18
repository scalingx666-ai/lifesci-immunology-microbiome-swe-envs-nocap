# Issue

**Title:** Added option to add a custom annotation, clarified multiQC results and fixed issues

## Description

<!--
# nf-core/viralrecon pull request

Many thanks for contributing to nf-core/viralrecon!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
-->
Included , issue #336 enhancements and issue 
- Added new param to add a custom annotation (gtf or gff format)
- Added new subworkflow to perform the additional annotation
- Allowed SNPEFF_BUILD process to detect wether annotation is in gtf or gff format
- Fixed variants_long_table so it won't select first annotation feature only, but remove the features that are not `upstream` or `downstream`
- Added a clearly description of variants_long_table formats and content for both nanopore and illumina.
- Clarify #SNPs and #INDELS in the illumina's multiqc

## PR checklist

- [X] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
- [x] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [X] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1883a68346f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.