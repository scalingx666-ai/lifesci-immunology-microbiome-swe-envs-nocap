# Issue

**Title:** Introduce different AgentPointer modes

## Description

Indirect mode:
The AgentPointer uses the unique AgentUid to identify an agent and obtain the raw agent pointer (`Agent*`).
This mode is necessary if the raw pointer changes during a simulation. For example, this can happen after sorting and balancing operations to optimize the memory layout.

Direct mode:
AgentPointer uses the raw agent pointer to identify an agent.
This mode is only possible for simulations where the raw agent pointer of an agent does not change during the simulation.
The direct mode improves the performance because the indirection to obtain the raw agent pointer is omitted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f2a503c32b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.