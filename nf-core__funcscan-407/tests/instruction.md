# Issue

**Title:** Fix comBGC: parsing multiple antiSMASH files

## Description

Symptoms before: Sometimes comBGC output contained correct BGC hits from antiSMASH, sometimes not.

2 reasons:
**1. comBGC level:** There was one indent level missing in a for loop, leading to only the last file of the supplied antiSMASH GBKs being parsed :melting_face: 
**2. pipeline level:** The output channel of the `antismash/antismashlite` module (which is input for comBGC) contains too many GBK files. We only want one file per sample (`<samplename>.gbk`), not all individual BGC-region GBKs (multiple files like `k141_1214065.region001.gbk`). This is fixed now by comBGC excluding files with the `region[0-9][0-9][0-9]` pattern in their names.

One could also fix **2.** by applying a more specific glob pattern on module level, which I didn't get to work. For example, `!(*region[0-9][0-9][0-9]).gbk` does the job if applied in bash terminal manually, but somehow not when applied via the module's main.nf like `tuple val(meta), path("${prefix}/!(*region[0-9][0-9][0-9]).gbk")    , emit: gbk_input
`:shrug: 

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,singularity --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `887d06db8079`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.