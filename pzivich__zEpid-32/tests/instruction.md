# Issue

**Title:** Gformula sequential

## Description

In reference to #30 

Dividing ``TimeVaryGFormula`` into two different estimation methods. Monte Carlo (currently implemented) and Sequential Regression (new method). Monte Carlo works better for survival data while Sequential Regression works best for longitudinal data

Sequential regression uses the following process
1) at Q_t fit a regression model to those who survived till T=t.
2) predict Y_t based on that model for the intervention of interest
3) for those who followed the treatment plan AND had the outcome they have a 1 carried forward
4) all else who did NOT have the outcome, are considered censored (np.nan)
5) above process is repeated. For those WITH predicted outcomes, their predicted outcome is used in the model fitting. Those who were observed at Q_{t-1} but censored at Q_t have their observed outcome used

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32b323a1a0b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.