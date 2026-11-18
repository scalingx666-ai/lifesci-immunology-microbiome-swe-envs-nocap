# Issue

**Title:** Build docker on push to master

## Description

What this does
---
- Adds a CI job that runs on master that publishes a package to the github package registry
- It can then be fetched using `docker.pkg.github.com/InstituteforDiseaseModeling/covasim/covasim:latest`
- Example on my fork is here: https://github.com/jules2689/covasim/packages/179707
- Here is how it looks in Actions running: https://github.com/jules2689/covasim/actions/runs/75647459

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6518eb09ffa0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.