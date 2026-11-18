# Issue

**Title:** Identify partly cyclic chains by compound-entry topology

## Description

KEGG pathway network walking (`anvio/kgmlnetworkops.py`) identifies linear and cyclic chains of reactions. "Partly cyclic" chains are a linear segment joined to a cycle by a branching reaction that appears both at the cycle entry/exit and as the chain's last reaction. The position of the branching reaction in the chain is now identified differently, not by reoccurrence of the same KGML reaction element, but upon encountering any reaction with the same compound-entry endpoints. Two KGML reaction elements connecting the same compound entries (e.g., alternative KOs for the same KEGG reaction) are now recognized as the same branching reaction. Previously, a chain was missed in partly cyclic branch computation if the cycle entry and close were encoded by different elements representing the same reaction.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6761eb3a8360`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.