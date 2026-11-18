# Issue

**Title:** Require -o argument in design.py

## Description

Previously, the `-o/--output-probes` argument was optional. This
could be desired if the goal was only to determine the number
of probes: even if the probe set is designed in order to compute
this number, one could simply leave out `-o` to ignore the probe
set. But this might be confusing, since a user could easily
run `design.py` to design a probe set, and find out after it runs
that the probe set was not output. It could also be wasteful
because `design.py` is sometimes computationally expensive to run
and a user could mistakenly leave out `-o`.

To avoid these issues, this commit changes the output argument
to be required.

This also updates the README to account for `-o` now being
required.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8003d3f91360`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.