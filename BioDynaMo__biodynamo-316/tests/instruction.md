# Issue

**Title:** Enable double precision in OpenCL kernel when compatible GPU is found

## Description

If a device has multiple GPUs with different floating precision capabilities, only the first GPU's capability is considered. This could lead to double-precision-enabled GPUs being ignored and thus resulting in BioDynaMo not using that GPU.

With this PR we check each GPU for it's FP-precision capability and choose the one that is requested for. If no compatible GPU is found, we throw a Fatal to inform the user that BioDynaMo should be compiled for lower precision.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff910d19bc9a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.