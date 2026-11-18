# Issue

**Title:** Fix checkm_download_url blocking parameter validation unconditionally

## Description

<!--
# nf-core/mag pull request

Many thanks for contributing to nf-core/mag!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/mag/tree/main/docs/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Description

`checkm_download_url`'s schema entry declares `"exists": true` on a non-null default (a Zenodo URL). nf-schema validates that unconditionally at pipeline startup, regardless of whether `--run_checkm` is actually enabled — unlike every other optional database param in this section (`checkm2_db`, `gtdb_db`, `cat_db`, ...), which default to `null` and are only validated when supplied.

That means **every single nf-core/mag run has a silent, unconditional dependency on Zenodo being reachable**, whether or not CheckM1 is used at all. Hit this independently on two different networks while trying to run `--run_checkm2` (not `--run_checkm`) during unrelated work — Zenodo was briefly unreachable from both, and the pipeline failed at parameter validation before a single process ran.

Reproduces deterministically, independent of Zenodo's actual availability:

```
nextflow run . -profile test_minimal --checkm_download_url /does/not/exist
```

### Fix

Drop `exists: true`. The real existence check already happens correctly at the point of actual use — `file(params.checkm_download_url, checkIfExists: true)` in `subworkflows/local/bin_qc/main.nf`, inside the `run_checkm` branch — so nothing is lost when `--run_checkm` is genuinely enabled with a bad URL; it just stops being checked when the feature isn't even on. `format: file-path` is kept (harmless, preserves documentation value; doesn't affect the check, confirmed by testing with and without it — the `exists` key is what triggers validation).

### Test

`tests/test_checkm_download_url_validation.nf.test` uses `-preview` (skips executing any process, but still runs `PIPELINE_INITIALISATION`'s parameter validation) so the regression test exercises only what this bug affects, as cheaply as possible — no real task execution needed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01NJ75Ui2JZjJwJ7T7o5acvg

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07a8b41b8d2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.