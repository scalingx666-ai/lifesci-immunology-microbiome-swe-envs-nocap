# Issue

**Title:** Use HTTPS instead of FTP for downloading taxdb data

## Description

From #250

Binder can't download data from FTP websites (only git and https), but both links used in `data/createtaxdb.sh` also work over HTTPS (despite having `ftp.` in the URL...)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a1348be78bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.