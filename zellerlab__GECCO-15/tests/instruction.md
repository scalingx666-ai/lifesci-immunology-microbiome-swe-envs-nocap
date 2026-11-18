# Issue

**Title:** Fixed how overlapping genes are identified during training

## Description

Changed _mixins.py to fix how overlapping genes are identified during training.

Previous method:
```
cluster_start <= gene.start and gene.end <= cluster_end
```

Proposed method:
```
cluster_start <= gene.end and gene.start <= cluster_end
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ebcdc264fe6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.