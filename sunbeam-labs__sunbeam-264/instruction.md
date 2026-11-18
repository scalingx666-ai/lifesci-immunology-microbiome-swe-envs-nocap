# Issue

**Title:** Update dependency versions

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully

This PR updates a number of dependencies:
 - snakemake (5.5 to <5.7) [also ]
 - trimmomatic (0.3.6 to 0.3.9)
 - grabseqs (0.3.4 to 0.6.1)
 - removed temporary dependency for h5py (is now handled by kraken-biom)

I also updated the major version field of the CircleCI env file checksum--this is mostly redundant as the dependencies (and checksum) have changed anyway but it seems like this is probably the best practice going forward. This PR is related to and .

I've also added the env details for this branch to the `stable_env` dir--we haven't released 3.0 yet but in case anyone is having trouble getting the `dev` dependencies installed we can point them to that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bfa87f1eefe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.