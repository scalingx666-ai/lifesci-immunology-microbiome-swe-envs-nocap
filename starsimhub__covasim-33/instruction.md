# Issue

**Title:** Cache python packages in GH Actions

## Description

What this does
---
- This caches the packages from between builds, it is hashed against `requirements.txt`
- This installed pytest and setuptools installs to `~/.cache/site-packages` for easy caching
- Saves time in CI. *We will not see the benefits on this PR as the cache has just been set*

What gains do we get here?
---
- About 40-50 seconds! (Keep in mind this is _after_ the first cache has been set)
- Latest master ran in 2m41s to 2m47s with `install covasim` taking about 53s: <img width="683" alt="image" src="https://user-images.githubusercontent.com/3074765/78323081-c151b100-753e-11ea-8c33-8c86d588b85d.png">
- With the cache, I ran in 2mXs to 2mXs with `install covasim` taking about 10s. The test step was also cut down by about 6s as pytest is also cached : <img width="635" alt="image" src="https://user-images.githubusercontent.com/3074765/78324534-f102b800-7542-11ea-9998-47c4d762d2df.png">


Other Thoughts
---
- It seems that our `setuptools` script is implicitly using `easy_install`, which is deprecated, so we might want to look into doing a `pip` install instead?
- We may want to add versions to our `requirements.txt` as the current setup is implicitly locking us to a version with the current cache

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cfc73005f97a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.