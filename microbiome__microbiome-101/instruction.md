# Issue

**Title:** Updated the R in DESCRIPTION and travis.yml files.

## Description

Travis CI now builds for various versions of R:
```yaml
 r:
 - release
 - oldrel
 - 3.3.3
 - 3.3.2
 - 3.3.1
 - 3.3.0
```

The package now depends on R >= 3.3.0:
```yaml
 Depends:
    R (>= 3.3.0),
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5eaadbb3f378`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.