# Issue

**Title:** Remove hack

## Description

* [x] I have run `pytest .tests/` on a local deployment and the tests passed successfully
* [x] If this adds a new output file, I have added a check to `.tests/targets.txt`
* [x] If this fixes a bug, I have added or modified an appropriate test
* [x] If this adds or modifies a rule that uses FASTQ files, the input accepts gzipped FASTQ and outputs gzipped FASTQ, or marks uncompressed FASTQ output as `temp`

If this is for a release:
* [x] I have updated documentation
* [x] I have updated all conda pin files (`snakedeploy pin-conda-envs workflow/envs/*.yml`)
* [x] I have updated the hardcoded version at the top of `install.sh` to match what this release's version will be
* [x] I have created a release archive that will be attached to this release (`bash dev_scripts/generate_archive.sh`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4a7a5cb22a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.