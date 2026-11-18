# Issue

**Title:** Silence NumPy warning about float subnormals

## Description

The dependency pyhmmer is compiled with -funsafe-math-optimizations. Loading a lib compiled with that flag will set some flags in the CPU for the whole process, which changes float subnormal behaviour.
This is detected when loading NumPy, raising a warning. I believe this is not an issue for Vamb, so I just silence the warning for now. I'm not too happy with this "solution".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c92334765432`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.