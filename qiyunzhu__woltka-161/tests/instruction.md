# Issue

**Title:** fixed collapse field 1 bug

## Description

The bug was as follows: if a profile is stratified, and the user wants to collapse based on the first field, the command should be:

```bash
woltka tools collapse -i input.biom -f 1 -m mapping.txt -o output.biom
```

But it wouldn't work, because Woltka mistakenly thought field code "1" means no field.

This bug is now fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71e4ae1e3eda`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.