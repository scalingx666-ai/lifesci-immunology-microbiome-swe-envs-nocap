# Issue

**Title:** Update docker RGI to use conda install

## Description

While I was in docker headspace I remembered I hadn't updated this image in quite a while.

It now installs in the docker container from conda (so as long as that works the container can easily be updated by running docker build on the Dockerfile as in the README).

I've also pushed a 5.1.0 container to dockerhub under the same finaymaguire/rgi as in the README

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `564e04853284`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.