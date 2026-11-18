# Issue

**Title:** Fix path bug:

## Description

Add a '/' to allow proper wildcard expansion.

Currently gives `No such file or directory` error: 
```
cp: cannot stat '/hifiasm/pb-metagenomics-tools/HiFi-MAG-Pipeline/4-DAStool/Sample/Sample_DASTool_bins*.fa': No such file or directory
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57207ac6c31f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.