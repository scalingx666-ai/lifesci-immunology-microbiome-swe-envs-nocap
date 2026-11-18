# Issue

**Title:** Fix deprecated np.bool in prodigal_biolib.py

## Description

This breaks in Python 3.8+ since `np.bool` has been deprecated in favour of builtin `bool`.

Would love if you could backport this to `2.1.1` (or a `2.1.2` release) so we can use the new features!

```
File "/mnt/tools/tool_dependencies/_conda/envs/__gtdbtk@2.1.1/lib/python3.8/site-packages/gtdbtk/biolib_lite/prodigal_biolib.py", line 378, in __build_coding_base_mask
    coding_base_mask = np.zeros(self.last_coding_base[seq_id], dtype=np.bool)
  File "/mnt/tools/tool_dependencies/_conda/envs/__gtdbtk@2.1.1/lib/python3.8/site-packages/numpy/__init__.py", line 284, in __getattr__
    raise AttributeError("module {!r} has no attribute "
AttributeError: module 'numpy' has no attribute 'bool'
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `adceaba4f1e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.