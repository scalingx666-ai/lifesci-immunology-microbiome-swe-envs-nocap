# Issue

**Title:** rename MinHash.containment to MinHash.contained_by

## Description

requires new install of sourmash:

```
pip install -U https://github.com/dib-lab/sourmash/archive/spacegraphcats.zip
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1de320cf11fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.