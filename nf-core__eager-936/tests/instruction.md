# Issue

**Title:** Patch 2.4.6

## Description

# [2.4.6] - 2022-11-14
## Added
 -  Added support for customising --seq-length in mapDamage rescaling (♥ to @ashildv for requesting)
## Fixed
 - Changed endors.py license from GPL to MIT (♥ to @aidaanva for fixing)
 - Removed erroneous R2 in single-end example in input TSV of usage docs (♥ to @aidaanva for fixing)
 Fixed read group incompatibility by re-adding picard AddOrReplaceReadGroups for MultiVCFAnalyzer (♥ to @aidaanva, @meganemichel for reporting)
 - Fixed edge case of DamageProfiler occasionally requiring FASTA index (♥ to @asmaa-a-abdelwahab for reporting)
 Increased significance values in general stats table for Qualimap mean/median coverages (♥ to @neija2611 for reporting)
 - Fixed parameter documentation for --snpcapture_bed regarding on-target SNP stats to state these stats currently not displayed in MultiQC only in the Qualimap results (♥ to @meganemichel and @TCLamnidis for reporting)
 Fixed broken parameter setting in mapDamage2 rescale length (♥ to @ashildv for reporting)
## Dependencies
 - Updated MultiQC to official 1.13 version (rather than alpha)
 - Added pinned MALT dependency to ensure working version in future versions of eager
## Deprecated
<!--
# nf-core/eager pull request

Many thanks for contributing to nf-core/eager!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/eager/tree/master/.github/CONTRIBUTING.md)
-->
<!-- markdownlint-disable ul-indent -->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42c9d5f8602e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.