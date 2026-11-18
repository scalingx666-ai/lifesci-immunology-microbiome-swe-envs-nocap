# Issue

**Title:** Update version

## Description

Hi!
I have noticed that a new version 3.0 has been tagged, nevertheless I think the version number has not been changed in the scripts.
- Also, this tagged version doesn't include the fix of 
`Fix issue causing bracken-build to error out if database.kraken exists`. Could it be that the version was tagged [22 Jul 2024](https://github.com/jenniferlu717/Bracken/releases/tag/v3.0) and the fix was merged , , 

I haven't changed the CHANGELOG as I'm not sure if you have a specific format to do it, but I guess should be also modified to include the updates of version 3.0, or if there is other file which also contains the version. 

I have suggested to bump it to version 3.0.1 as it has been already released 3.0 in [bioconda](https://anaconda.org/bioconda/bracken/files)

I would very much appreciate it if you could update the version and the bioconda package with the bracken-build fix included.

Thank you very much in advance!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05d695c5a8c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.