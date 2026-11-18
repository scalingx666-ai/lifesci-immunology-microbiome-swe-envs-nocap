# Issue

**Title:** Patch Release 2.4.3

## Description

Patch release 2.4.3

### `Fixed`

-  Improved error message if required metagenomic screening parameters not set correctly
-  Remove deprecated parameters from test profiles
-  Fix --snpcapture_bed files not being picked up by Nextflow (❤ to @meganemichel for reporting)
-  Re-add direct piping of AdapterRemovalFixPrefix to pigz
-  Fixed reference masking prior to pmdtools
-  Updates parameter documention to specify `-s` preseq parameter also applies to lc_extrap
-  Fixes a file-name clash during additional_library_merge, post-BAM trimming of different UDG treated libraries of a sample
- Renamed a range of MultiQC general stats table headers to improve clarity, documentation has been updated accordingly
-  Corrected samtools fastq flag to _retain_ read-pair information when converting off-target BAM files to fastq in paired-end mapping (❤ to @alexhbnr for reporting)
-  Corrected tutorials to reflect updated BAM trimming flags (❤ to @marcel-keller for reporting)

### `Dependencies`

-  Bumped sequencetools: 1.4.0.5 -> 1.5.2
- Bumped MultiQC: 1.11 -> 1.12 (for run-time optimisation and tool citation information)


## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
    - [ ] If you've added a new tool - add to the software_versions process and a regex to `scrape_software_versions.py`
    - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](<https://github.com/>nf-core/eager/tree/master/.github/CONTRIBUTING.md)
    - [ ] If necessary, also make a PR on the nf-core/eager _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e15d66698948`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.