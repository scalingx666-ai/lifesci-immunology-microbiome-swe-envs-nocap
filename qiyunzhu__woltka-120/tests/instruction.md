# Issue

**Title:** Fixed free-rank classification no target issue

## Description

Previously, with free-rank classification, if the subject is not found in the classification system, the program will raise an error. However, some realistic classification system don't work that way. For example, the following command:

```bash
woltka classify -i input.sam -c coords.txt -m metacyc.map -o output.tsv
```

Will fail if one or more ORFs are not found in the mapping file, which is highly likely.

This issue was found by @droush .

This patch allows the program to bypass (more specifically, return `None`) these instances.

It may slow down the algorithm marginally, though.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `596aa87b9aa6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.