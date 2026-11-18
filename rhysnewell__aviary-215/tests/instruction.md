# Issue

**Title:** Add pyproject.toml.

## Description

Addresses the warning described at 


I think this is just a simple hoop to jump through? The warning I got when running `pip install -e .` went away, and aviary seems to work run afterwards.

```
Installing collected packages: aviary-genome
  DEPRECATION: Legacy editable install of aviary-genome==0.9.2 from file:///mnt/hpccs01/home/woodcrob/git/aviary (setup.py develop) is deprecated. pip 25.0 will enforce this behaviour change. A possible replacement is to add a pyproject.toml or enable --use-pep517, and use setuptools >= 64. If the resulting installation is not behaving as expected, try using --config-settings editable_mode=compat. Please consult the setuptools documentation for more information. Discussion can be found at 
```

Not sure I quite understand everything that is going on here though..

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2664ca1f419d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.