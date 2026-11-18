# Issue

**Title:** Support parametrized optional FCS keywords

## Description

Adds support for setting `$Pn[DFLOPTV]` and `$PnCALIBRATION`. Skips the deprecated keywords (`$Gn*`, `$PKn`, `$PKNn`) and the rarely used ones (`$RnI`, `$RnW`, `$CSVnFLAG`).

FlowKit test run: https://github.com/primitybio/FlowIO/actions/runs/3130423878

---

Last PR for now. There are a few other changes I'd consider, but none are pressing:
- Don't upper-case all keys. Some importers are erroneously case-sensitive, so this can break those. Mixed case can also be easier to read as a human (things like `P2DetectorName`).
- Use a different delimiter than `/` since that's also found in file paths and the source of many invalid FCS files.
- Allow zero-length files. They're valid and sometimes useful.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79ce5847c029`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.