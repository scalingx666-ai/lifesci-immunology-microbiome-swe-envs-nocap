# Issue

**Title:** Add different time units to `ProgressBar`

## Description

```
 ET = Elapsed Time; TR = Time Remaining
 [##################################################] 500 / 500 ( ET: 9310.000000, TR:0.000000)[ms]
 
 ET = Elapsed Time; TR = Time Remaining
 [##################################################] 500 / 500 ( ET: 9.05, TR:0.0)[s]
 
 ET = Elapsed Time; TR = Time Remaining
 [##################################################] 500 / 500 ( ET: 0.154600, TR:0.000000)[min]

[...]

 ```

To test: just go to the `analytic_continuum` demo and test different values for 
```
"progress_bar_time_unit": "X",
```
in bdm.json. (X=ms,s,min,h)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80e047817326`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.