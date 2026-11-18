# Issue

**Title:** WIP: support running CHIME under Habitat

## Description

@themightychris, here's a very rough PR. Should work for things like:
```
hab sup run bixu/chime
 # or
hab svc load bixu/chime
```

I'm working on wiring up my fork's `master` branch to demo how Builder could build and serve a `stable`-channel version of the package.

Still on my wishlist:
  - Windows Plan
  - Running inside of a "shim" container (like `bixu/hab:latest`) and configuring with env vars

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74defe5eadeb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.