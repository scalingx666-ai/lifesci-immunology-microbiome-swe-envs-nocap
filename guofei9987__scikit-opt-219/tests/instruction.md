# Issue

**Title:** Update GA.py to add class EGA to achieve GA with elitist machine

## Description

define class EGA from GA;

`self._n_elitist = n_elitist` in `__init__()`;

redefine run() in EGA, in each iteration, isolate top n fitted elitists out from population, add them back after selection(), crossover() and mutation().

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98d4270d7ee8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.