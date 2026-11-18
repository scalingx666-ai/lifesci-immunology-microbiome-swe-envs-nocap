# Issue

**Title:** Ensure column ordering on `get_mag_depths.py`

## Description

This PR address an issue I found when working on the snapshots.
In some (machine dependent?) cases, the `get_mag_depths.py` would not produce consistent column ordering on depth summaries, and as we are merging them the dummy way via `.collectfile(keepHeader: true)`, that could result in partially swapped results in the final summary.

Example of the outcome (same test, different machines):
<img width="2199" height="277" alt="image" src="https://github.com/user-attachments/assets/5247c087-4c19-4a21-b018-1823b0a53753" />

I also improved the script a little to make it easier on the eyes.

## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46f806834bfd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.