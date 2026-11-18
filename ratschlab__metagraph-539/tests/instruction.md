# Issue

**Title:** Also include metagraph_DNA5 in the docker image (for search with Ns)

## Description

solves #480

Usage:
```
docker run -v ../tests/data/:/mnt --entrypoint metagraph_DNA5 <IMAGE>     build -v -k 10 -o /mnt/transcripts_1000 /mnt/transcripts_1000.fa
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24859285ca3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.