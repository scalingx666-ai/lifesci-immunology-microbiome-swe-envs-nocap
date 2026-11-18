# Issue

**Title:** Add --max_ee_r to set DADA2 maxEE separately for reverse reads

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
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Description

.

On paired-end Illumina data, `--max_ee` currently applies to both forward and reverse reads via one shared `filterAndTrim(maxEE = c(x, x))` call. Some sequencing runs show a quality drop restricted to the reverse read only (a known Illumina NextSeq behaviour, per the issue), for which a single shared threshold forces an unwanted trade-off between the two reads.

This adds `--max_ee_r`, which lets the reverse read use its own, typically more permissive, expected-error threshold instead — mirroring the existing `--trunclenf`/`--trunclenr` precedent for separate forward/reverse truncation lengths.

- `--max_ee_r` unset (default): behaviour is unchanged. `conf/modules.config`'s new ternary renders byte-identical `ext.args` output to before, and `default.nf.test`'s snapshot needed no update.
- `--max_ee_r` set: overrides `--max_ee` for the reverse read only, for paired-end Illumina data (the only sequencing type with a separate reverse read in the first place).
- `modules/local/summary_report.nf` / `assets/report_template.Rmd`: the report now states forward/reverse thresholds separately when `--max_ee_r` is set, instead of always reporting one shared value.

### Test coverage

Added a small, dedicated `test_max_ee_r` profile (`conf/test_max_ee_r.config` + `tests/max_ee_r.nf.test`) rather than a module-level `nf-test` for `DADA2_FILTNTRIM`. This repo's local modules are flat single-file, and a module-level test would require converting to the nested `main.nf`/`meta.yml`/`tests` layout that only vendored `modules/nf-core/**` components use — and this repo's own `nf-test.config` explicitly ignores tests under that path, so it wouldn't even run in CI. The new profile skips taxonomy and QIIME2 entirely (not needed to exercise DADA2 read filtering), keeping it one of the cheaper test profiles in the suite (~2.5 min locally), and asserts directly on the published `dada2/args/filterAndTrim.args.txt` content.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `827a6b77be8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.