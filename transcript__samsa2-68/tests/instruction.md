# Issue

**Title:** Error correction (package_installation.bash and full_database_download.bash, issues66)

## Description

From issue: 

1. Error meassage of package_installation.bash
command : bash setup_and_test/package_installation.bash
Error message : setup_and_test/package_installation.bash: line 38: ../bash_scripts/lib/common.sh: No such file or directory

2. Error meassage of full_database_download.bash
command : bash setup_and_test/full_database_download.bash
Error message : setup_and_test/full_database_download.bash: line 32: ../bash_scripts/lib/common.sh: No such file or directory

Hence, I suggest to fix package_installation.bash (and full_database_download.bash) as shown below.

`if [[ -d "${BASH_SOURCE%/*}/../bash_scripts/lib/common.sh" ]]; then`
->
`if [ -d "${BASH_SOURCE%/*}/../bash_scripts/lib/" ]; then`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa7819a6a73c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.