# Issue

**Title:** Various testing and dependency fixes

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully
* [ ] ~~If this adds a new output file, I have added a check to tests/targets.txt~~
* [X] If this fixes a bug, I have added an appropriate test to tests/test.sh
* [ ] ~~If this adds or modifies a rule that uses FASTQ files, the input accepts gzipped FASTQ and outputs gzipped FASTQ, or marks uncompressed FASTQ output as `temp`~~

This addresses a few different things to get our tests passing again:

 * Allow the use of [mamba](https://github.com/mamba-org/mamba) as an alternate dependency solver and use it for CircleCI testing.  This is so that the automated tests can install the environment in a reasonable amount of time (and real installs too, with `./install.sh -m`) and with lower RAM usage.  If mamba is already installed it will be used to set up the environment.
 * Require megahit >1.1.2 as we all <1.2.  Recently the dependency resolution has been installing the earliest available megahit package on bioconda, which incidentally has all of its executables stored at the top level of the environment instead of in `$CONDA_PREFIX/bin`.  This ensures that version won't get installed and in the long run we'll probably raise the minimum anyway when migrating to newer megahit.
 * Fixes the coverage.csv checks in `test_mapping`.  These were silently failing because of explicit zero-read rows in phix's coverage table instead of missing rows, and a lack of an error message made it extra confusing to figure out.  Now the test matches the actual output, and if it fails, shows an error message.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6500fcab4546`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.