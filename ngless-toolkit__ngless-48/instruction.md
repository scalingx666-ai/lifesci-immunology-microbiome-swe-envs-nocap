# Issue

**Title:** ENH+DOC+TST Implement reference aliases and update supported references

## Description

The following genome reference identifiers were disambiguated since they represent different assemblies:

    - hg38.p7  (was hg38)
    - hg38.p10 (added)
    - mm10.p2  (was mm10)
    - mm10.p5  (added)

The following were renamed as their common names did not match the version used:

    - canFam3 (was canFam2)
    - dm5     (was dm3)
    - rn5     (was rn4)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e469ac8249c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.