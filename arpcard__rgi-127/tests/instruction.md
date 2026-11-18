# Issue

**Title:** Load all databases in docker image/file

## Description

As per the idea from @nebfield I've updated the `Dockerfile` to install all the databases.

Only minor issue is there is no easy way to check what version of wildCARD/CARD R&V has been downloaded so the version isn't correct.  @raphenya don't suppose you can add a file that contains the version metadata the wildCARD/CARD R&V tarball? 

This also adds a github action to autobuild the container on a new release, but I'm not totally sure this will work seamlessly so might need some tinkering @raphenya

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ac796e260cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.