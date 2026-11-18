# Issue

**Title:** Add ProgressBar to visualise progress in `Simulate()`

## Description

Added a ProgressBar such that one clearly sees the progress of the simulation. Example output:
```
ET = Elapsed Time; TR = Time Remaining
[######                                          ] 135 / 1000 ( ET:  1649, TR:10566)[ms]
```

Examples:
1. No output (default)
```
[bdm-1.3.4] (base) 
~/tmp/soma_clustering/build on  master! ⌚ 12:34:13
$ ./soma_clustering
number of cells in subvolume: 2360
average neighbors in subvolume: 28
correctness coefficient: 0.0157542
Simulation completed successfully!
```

2. Show Simulation step every 100 steps
```
[bdm-1.3.4] (base) 
~/tmp/soma_clustering/build on  master! ⌚ 12:36:10
$ ./soma_clustering  --inline-config '{ "bdm::Param": { "show_simulation_step": 100 } }' 
Time step: 0
Time step: 100
Time step: 200
Time step: 300
Time step: 400
Time step: 500
Time step: 600
Time step: 700
Time step: 800
Time step: 900
number of cells in subvolume: 2384
average neighbors in subvolume: 26
correctness coefficient: 0.0468571
Simulation completed successfully!
```

3. Use the progress bar
```
~/tmp/soma_clustering/build on  master! ⌚ 12:34:29
$ ./soma_clustering  --inline-config '{ "bdm::Param": { "use_progress_bar": true } }'

ET = Elapsed Time; TR = Time Remaining
[##################################################] 1000 / 1000 ( ET: 11988, TR:    0)[ms]
number of cells in subvolume: 2456
average neighbors in subvolume: 26
correctness coefficient: 0.026382
Simulation completed successfully!
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2750867f7a48`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.