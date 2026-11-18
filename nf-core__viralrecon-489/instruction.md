# Issue

**Title:** Switch CI to self hosted runners and update minimal nextflow version

## Description

![image](https://github.com/user-attachments/assets/079055ac-863b-4124-a2d3-e1fbdac5f9da)

Awesome with your thorough pipeline tests! Unfortunately they eat up more than twice of our allotted GitHub Runners. Switching them to self-hosted runners should remove that load, while requiring no further changes on your side (if everything works as expected).

Also needed to update the minimum nextflow version, to avoid `java.nio.channels.OverlappingFileLockException` which was fixed in `>24.02.4`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `02a8be5239aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.