# Issue

**Title:** Add dedicated optitype output folder.

## Description

<!--
# nf-core/hlatyping pull request

Many thanks for contributing to nf-core/hlatyping!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/hlatyping/tree/master/.github/CONTRIBUTING.md)
-->

## Description

Currently, the results of optitype get stored in the `params.outdir` folder (i.e. `results`) by sample, alongside other tool outputs (e.g. `multiqc`, `fastqc`, `pipeline_info`). It would be neater if it were stored by default in the folder `${params.outdir}/optitype`. While this is a sort of a subjective decision, it would be necessary if other tools were added in the future, to distinguish the tools output. It can still be overridden if needed by the users custom configs.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/hlatyping/tree/master/.github/CONTRIBUTING.md)- [ ] If necessary, also make a PR on the nf-core/hlatyping _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `468cd6b6d002`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.