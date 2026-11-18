# Issue

**Title:** feat(docker): Dockerfile updated

## Description

@AlphaSquad 

I updated the Dockerfile and added a requirements.txt ( )
I also registered CAMISIM on Dockerhub.
CAMISIM will be build on updates on the dev/master branch and also if a new release is made.
Updates on the master branch are tagged as latest (cami/camisim:latest).
Updates on the master branch are tagged as dev (cami/camisim:dev).
Release tags are directlry  translated to docker tags (cami/camisim:1.0.0).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8531edb42e4f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.