# Issue

**Title:** update to release v1.1.0

## Description

- Add read ANI to clustering algorithm to break ties for related exemplars with equal read count. This, as far as I can tell, now makes the EsViritu ouputs deterministic.
- Remove deprecated distutils module for shutil.which
- Add estimated read ANI to assembly table outputs
- Fix reactable title for project summary htmls
- Add info on downloading latest DB (v3.2.2)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74be556c0be9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.