# Issue

**Title:** add cli

## Description

@inc0 @cliffckerr per our discussion adding cli entrypoints in `/script`. This PR should close #8 

## Two entry points

### `python script/sim.py` Examples

To run simulation with default parameters:
> python sim.py

To run simulation with an intervention:
> python sim.py --interv=True

To run simulation with an intervention and save plot to disk:
> python sim.py --interv=True --do_save=True

To run simulation with custom configuration
> python sim.py --pars "{pop_size:20000, pop_infected:1, n_days:360, rand_seed:1}"

### `python script/scenarios.py` Examples

To run the scenario with default parameters
> python scenarios.py

To run simulation with a custom configuration:
> python scenarios.py --basepars "{pop_size: 5000}" --metapars "{n_runs:3, noise:0.1, noisepar:'beta', rand_seed:1, quantiles:{'low':0.1, 'high':0.9}}"

To run simulation with an intervention changing social distancing duration and effectiveness:
> python scenarios.py --interv_day=35 --interv_eff=0.7

To run simulation and save plot to disk:
> python scenarios.py -do_save=True

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a489c0f6a019`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.