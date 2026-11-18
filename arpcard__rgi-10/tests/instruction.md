# Issue

**Title:** Integrate Docker build option into RGI

## Description

Add Dockerfile to allow local and automated Dockerhub dockerbuilds

Automatic Dockerhub builds currently build under my dockerhub account but can be configured for an CARD dockerhub account fairly easily (`https://docs.docker.com/docker-hub/builds/`).

Updated documentation to explain how to use docker version of RGI

Should resolve #9

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fafd908defde`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.