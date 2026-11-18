# Issue

**Title:** V0.4.2

## Description

Updating to version 0.4.2

- [x] ``TMLE`` calculates all implemented measures (RD, RR, OR) at once. Saves computation time if the user wants multiple measures and is fitting a time-intensive ML algorithm #39

- [x] Fixing ``standard_mean_difference`` for categorical variables. Will need to use patsy to parse out categorical variables via ``C(...)``, otherwise "I" cannot know which variables are categorical #59 

- [x] Adding stochastic treatments for binary exposures for ``TimeFixedGFormula`` via ``fit_stochastic()`` Allows for both unconditional and conditional probablities #58 

- [x] ~~Add continuous outcomes to ``TimeFixedGFormula`` but this time actually get it to work as intended. Need to think through the set up for the two potential interventions (threshold vs. shift)~~ delaying this again... #49

- [ ] Also learn ReadTheDocs for the Reference papge (still not doing what I hoped it would)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c513c70df96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.