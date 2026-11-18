# Issue

**Title:** Update ivar_variants_to_vcf.py: Bug Fixes, Merging Improvements & Refactor

## Description

**Description:**
This PR introduces several updates and fixes to ivar_variants_to_vcf.py, improving variant merging, filtering, and overall script performance.

**Key Changes:**
- Fixed variant deletion bug – Close variants were being removed incorrectly after merging.
- Refactored merging rules – Improved handling of variant combinations.
- Ref DP-based ref AF calculation – Ensures reference allele frequency is properly computed.
- Improved duplicate handling – Duplicates are now removed before analysis.
- Better filtering logic – Consensus haplotypes and references with zero depth (ref_DP = 0) are now skipped.
- Enhanced readability & linting – General code cleanup and style improvements.

**Related Issues:**


<!--
# nf-core/viralrecon pull request

Many thanks for contributing to nf-core/viralrecon!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)- [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ddf1c296ff5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.