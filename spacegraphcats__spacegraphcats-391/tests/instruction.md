# Issue

**Title:** [MRG] support randomizing unitig order via config parameter.

## Description

This adds a config parameter to randomly re-order the cDBG nodes, `cdbg_shuffle_seed`.

This can be set in the config file like so:

```yaml
cdbg_shuffle_seed: 42
```
The default is `42`, which is tied to the default seed parameter in sourmash `MinHash` objects.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8ed3249f6a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.