# Issue

**Title:** Fix bam filtering

## Description

While testing CircularMapper, I found out that providing `--fasta_largeref` caused half the pipeline to not execute. The reason was that BAM filtering once accounts for the BAI indices, so I made changes so the CSI indices are also picked if necessary.

A similar bug was also identified in the nf-core SWF BAM_SPLIT_BY_REGION, so I deactivated the `-c` option for SAMTOOLS_INDEX in that SWF, to avoid issues. The swf will need an upstream fix, but since we don;t publish these indices, it makes little difference here.

Also fixed the same issue when running flagstat on input bams
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
- [ ] If you've fixed a bug or added code that should be tested, add tests!
    - [ ] If you've added a new tool - add to the software_versions process and a regex to `scrape_software_versions.py`
    - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](<https://github.com/>nf-core/eager/tree/master/.github/CONTRIBUTING.md)
    - [ ] If necessary, also make a PR on the nf-core/eager _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e0fe5ebfabb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.