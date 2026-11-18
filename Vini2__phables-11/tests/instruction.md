# Issue

**Title:** replace coverm

## Description

Replaces coverm. I also added resources to the config file. Just be aware that resources in the config is multi-level and if you want to make it parseable on the command line AND mergeable with the default config you'll need to replace the config merge funcion with a recursive one. the one we use for hecatomb is:
```python
import collections.abc
def recursive_merge_config(config, overwrite_config):
    def _update(d, u):
        for (key, value) in u.items():
            if isinstance(value, collections.abc.Mapping):
                d[key] = _update(d.get(key, {}), value)
            else:
                d[key] = value
        return d
    _update(config, overwrite_config)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10fb566821f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.