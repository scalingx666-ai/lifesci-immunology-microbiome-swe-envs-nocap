# Issue

**Title:** 128 - Healthcheck probe + startup time improvements for docker webapp

## Description

Addresses #128 
- Adds a GET api for healthchecks. 
In addition
- Pre-byte compile covasim python library in docker image for cluster environments(mainly for kubernetes)
- Cache Numba JIT commands, mainly for webserver environment (mainly for kubernetes)
- Add readiness/liveliness checks to kubernetes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `499db143834a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.