# Issue

**Title:** Fix database creation for GTDB r214

## Description

As mentioned in  the protein FASTA files in GTDB r214 are now individually compressed. Because the `mmseqs tar2db` command only includes files that finish wirh `.faa`, the protein files are being ignored and the database is not being created.

This PR just changes [this line](https://github.com/soedinglab/MMseqs2/blob/ad6dfc66d7bbc4fd626fc19adf10ba587bc137c4/data/workflow/databases.sh#L374) to change `--tar-include 'faa$'` to `--tar-include 'faa.gz$'`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad6dfc66d7bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.