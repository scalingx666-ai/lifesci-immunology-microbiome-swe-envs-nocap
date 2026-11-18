# Issue

**Title:** Fixed the Dockerfile

## Description

**Issue:** Docker-image is not working correctly for v2.0.0 (locally). And is not working on https://hub.docker.com/r/hadrieng/insilicoseq

- Updated the Dockerfile: The v2.0.0 docker image works. 
- Added script docker-build.sh: Builds a multi architecture Docker-image for AMD and ARM. @HadrienG I have left the REGISTRY value open in the script for you to fill in. I have tested the script on our docker-registry and as far as I could test it worked. Please let me know if it does the trick for you too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e335ca9ff1a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.