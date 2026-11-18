# Issue

**Title:** Expanded Conversion from BilayerNetwork to PetriNet

## Description

This PR addresses the problem that there are bilayer networks which do not trivially convert to an equivalent Petri net through functorial data migration. One such example is the following bilayer equivalent to the SIR Petri net model.
![image](https://user-images.githubusercontent.com/19711695/122827019-dafd2680-d2b1-11eb-9282-6afb4b73af7a.png)

The `balance!` function adds or removes pairs of Wn, Wa wires in order to allow for functorial data migration.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `534c987c7318`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.