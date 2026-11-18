# Issue

**Title:** Update qc.py for filter komplexity id bug

## Description

* [x] I have run `pytest .tests/` on a local deployment and the tests passed successfully
* [ ] If this adds a new output file, I have added a check to `.tests/targets.txt`
* [ ] If this fixes a bug, I have added or modified an appropriate test
* [ ] If this adds or modifies a rule that uses FASTQ files, the input accepts gzipped FASTQ and outputs gzipped FASTQ, or marks uncompressed FASTQ output as `temp`

If this is for a release:
* [ ] I have updated documentation
* [ ] I have updated all conda pin files (`snakedeploy pin-conda-envs workflow/envs/*.yml`)
* [ ] I have updated the hardcoded version at the top of `install.sh` to match what this release's version will be
* [ ] I have created a release archive that will be attached to this release (`bash dev_scripts/generate_archive.sh`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3254c84968e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.