# Issue

**Title:** Cover --max_ee_r in an existing test config instead of a dedicated test

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

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Description

, addressing @d4straub's review point that `--max_ee_r` should be covered by an
existing Illumina paired-end test config rather than by an additional test.

#1065 merged with a second `test()` block in `tests/default.nf.test`, which still costs a full extra
pipeline run on CI even though it no longer lives in its own file. This PR removes that block and
sets `max_ee_r = 5` in `conf/test_novaseq.config` instead — Illumina paired-end data, so the
parameter is genuinely exercised there. The existing `test_novaseq` test gains one assertion, that
`filterAndTrim` was called with `maxEE = c(2, 5)`, confirming `--max_ee_r` overrode `--max_ee` for the
reverse read only.

Net effect: same coverage, one fewer CI test.

### Changes

- `conf/test_novaseq.config` — `max_ee_r = 5`
- `tests/novaseq.nf.test` — assert `maxEE = c(2, 5)` in `dada2/args/filterAndTrim.args.txt`
- `tests/novaseq.nf.test.snap` — regenerated; the four DADA2 output checksums change, which is the
  expected consequence of more reverse reads passing the relaxed threshold
- `tests/default.nf.test` / `.snap` — the `-profile test, max_ee_r` block and its snapshot entry removed
- `CHANGELOG.md` — entry under `Changed`

### Verification

- `nf-test test tests/novaseq.nf.test --profile=+docker` passes
- `prek run -a` clean
- `nextflow lint .` reports no errors, both at the declared minimum (26.04.0) and at the current version
- `nf-core pipelines lint` currently fails on this repo for an unrelated, pre-existing reason
  (`nextflow config -o json` errors with `Cannot invoke method endsWith() on null object`, reproducible
  on a clean `dev` checkout)

Reviewed and implemented with help from Claude Code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2698b16abf5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.