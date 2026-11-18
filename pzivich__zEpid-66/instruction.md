# Issue

**Title:** v0.5.0

## Description

Version 0.5.0

Features to be implemented:

- [x] Replace AIPW with the more specific AIPTW #57 

- [x] Add support for monotone IPMW #55 

- [ ] ~~Add support for nonmonotone IPMW #55~~ As I have read further into this, it gets a little complicated (even for the unconditional scenario). Will save for later implementation

- [ ] Add support for continuous treatments in TimeFixedGFormula #49 

- [ ] ~~Add stratify option to measures #56~~

- [x] TMLE with continuous outcomes #39 

- [x] TMLE with missing data #39 (only applies to missing outcome data)

- [ ] ~~Add support for stochastic interventions into TMLE #52~~ Above two changes to TMLE will take precedence. Stochastic treatments are to be added later

- [ ] ~~Add support for permutation weighting (TBD depending on complexity)~~ Will open a new branch for this project. No idea on how long implementation may take

- [x] Incorporate random error in `MonteCarloRR`

Maintenance 

- [x] Add Python 3.7 support

- [x] Check to see if matplotlib 3 breaks anything. LGTM via `test_graphics_manual.py`

- [x] Magic-g warning updates for g-formula #63

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1aad530bf3bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.