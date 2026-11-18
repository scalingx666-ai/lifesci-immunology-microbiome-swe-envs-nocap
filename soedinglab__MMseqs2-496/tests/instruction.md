# Issue

**Title:** changing the url of UniRef* from ftp to https

## Description

Requesting from the current urls with ftp as protocol gives me error as follows:

`Invalid request. Privoxy doesn't support FTP.`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49c2b70b47a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.