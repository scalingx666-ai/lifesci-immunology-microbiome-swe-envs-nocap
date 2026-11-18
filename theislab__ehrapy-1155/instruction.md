# Issue

**Title:** Estimate the cumulative incidence of competing events in kaplan_meier

## Description

`ep.tl.kaplan_meier` takes an `event_of_interest` and then estimates its cumulative incidence with the Aalen-Johansen estimator, `ep.tl.nelson_aalen` the cause-specific cumulative hazard, and `ep.pl.kaplan_meier` plots the cumulative incidence. Event columns with competing events now raise without `event_of_interest` instead of silently being treated as one event.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6ef31a3ea49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.