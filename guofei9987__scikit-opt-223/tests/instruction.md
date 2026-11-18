# Issue

**Title:** Fix RuntimeError: context has already been set

## Description

After invoking torch.multiprocessing.set_start_method, importing sko will result in "RuntimeError: context has already been set". Here is a simple code to reproduce it(to be run in a non-win32 environment).

```python
import torch.multiprocessing as mp
mp.set_start_method("spawn")

import sko # <-- RuntimeError occurs.
```

This pull request should fix it. (Reference: <)
Possible related Issue: #146

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e5a1d118bd7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.