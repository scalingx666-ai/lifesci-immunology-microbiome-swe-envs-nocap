# Issue

**Title:** Replace `rm->AddAgent` with `ctxt->AddAgent` in demos

## Description

The call `rm->AddAgent` is not thread safe and users should typically use `ctxt->AddAgent`. With this PR, we change the demo code such that future uses will learn to use `ctxt->AddAgent`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c50e1ada4f8c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.