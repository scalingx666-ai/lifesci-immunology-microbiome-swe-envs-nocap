# Issue

**Title:** Fix: using files.wwpdb.org instead of ftp.wwpdb.org

## Description

Following #772: ftp.wwpdb.org is being deprecated. It does not accept http(s) requests anymore. Moving to the new FTP archive over HTTP service.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f45232ac8da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.