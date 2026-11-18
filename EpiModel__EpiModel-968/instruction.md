# Issue

**Title:** Address SG epiweb comments

## Description

## Summary
- **Task 1**: Restore differential death rates by compartment for DCM and ICM apps.
- **Task 2**: Make DCM app non-reactive with Run Model button. Fix preset race condition.
- **Task 3**: Fix plot sizing stability with fixed-height tab card and internal scrolling.
- **Task 4**: Keep `plotly` in Suggests (no code change).
- **Task 5**: Move Run Model button to header. Add Disease Type/Scenario accordion. Remove sidebar collapse toggle.
- **Task 6**: Incidence rate (always shown) + attack rate (conditional). Add Guide docs.
- **Task 7**: Add "and infectious" to SI model description.
- **Task 8**: Note in sensitivity analysis panel that range overrides fixed parameter value.
- **Task 9**: Clarify infection duration formula accounts for departure rate with vital dynamics.
- **Task 10-11**: ICM R0 interpretation uses "is expected to" language (stochastic).
- **Task 12**: Clarify R0 describes transmission from first infected in a fully susceptible population.
- **Task 13**: Change "Population" to "Initial Population" in summary config table.
- **Task 14-15**: Clarify preset time steps = days, standardize recovery descriptions to include both duration and rate.

## Test plan
- [x] DCM: Model only runs on button click
- [x] DCM/ICM: Presets stay selected
- [x] DCM/ICM: Differential death rate labels correct
- [x] DCM/ICM: Plot stable across tabs
- [x] DCM/ICM: Run Model button in header
- [x] DCM/ICM: Incidence metrics conditional logic correct
- [x] DCM/ICM: SI description says "infected and infectious"
- [x] DCM: Sensitivity analysis override note visible
- [x] DCM/ICM: Recovery rate Guide text mentions vital dynamics adjustment
- [x] ICM: R0 summary uses "is expected to" language
- [x] DCM/ICM: R0 text refers to first infected person
- [x] DCM/ICM: Summary table says "Initial Population"
- [x] DCM/ICM: Preset descriptions say "acts/day", include duration + rate
- [x] CI passes

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8dc21b7c7d73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.