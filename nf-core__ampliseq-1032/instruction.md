# Issue

**Title:** Move self-contained channel construction into PIPELINE_INITIALISATION

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Description

Part of #1029: moves the params that are used only to construct a channel (with no other logic depending on how it's built) out of `workflows/ampliseq.nf` and into `PIPELINE_INITIALISATION`, threading them down through `NFCORE_AMPLISEQ` -> `AMPLISEQ` as explicit `take:`/`emit:` arguments instead of reaching into global `params` directly.

- Moves 9 channels: `metadata`, `report_template`/`report_css`/`report_logo`/`report_abstract`, `pplace_sheet`'s initial value, `expected_sequences`/`expected_abundances`, `metadata_category`.
- Pure plumbing refactor, no behavior change.
- Adds a second test case to `tests/default.nf.test` for `--report_abstract` and `--metadata_category`, the two params among these that weren't exercised by any existing test profile.
- Also includes an unrelated fix: the vendored `cutadapt` module's `stub:` block referenced `${outformat}` without ever assigning it (only `script:` did), breaking `-stub-run`.

Deliberately out of scope for this PR (left for follow-up): the remaining scalar `params.X` reads in `workflows/ampliseq.nf`, the per-classifier reference-taxonomy channels (entangled with catalog-download logic), and `params.X` reaches inside `subworkflows/local` and `modules/local`.

Verified: `nf-test` (both cases pass, no snapshot changes), `nf-core pipelines lint`, `nextflow lint .` at 26.04.0 and 26.04.6 (0 errors both), `prek run -a`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `17a31e471f2e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.