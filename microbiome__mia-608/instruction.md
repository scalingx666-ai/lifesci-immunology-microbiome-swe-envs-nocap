# Issue

**Title:** Package loading message

## Description

Some packages have a message when package is loaded into the session. Do we want that kind of thing? It could give info on online documentation. Currently, this PR implements the following message.

```
> library("mia")
ℹ Loading mia
This is mia version 1.13.30
- Online documentation and vignettes: https://microbiome.github.io/mia/
- Online book 'Orchestrating Microbiome Analysis (OMA)': https://microbiome.github.io/OMA/docs/devel/
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `50bd2ea9b6e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.