# Issue

**Title:** Add a 10k SIS reference case for netsim() run time, with a timing guard

## Description

- Now: there is no fixed case for comparing run time before and after a change. Each PR in the run-time program built its own.
- Goal: one small reference case and one table, so that "sis-10k: 19.7 to 18.2 ms per step" in a PR means the same thing every time. Second piece of the harness in EpiModel/EpiModelHIV-p#428.
- How: `inst/bench/sis-10k.R` runs a 10,000-node SIS model (five-term formation model, tergmLite, arrivals and departures, 100 steps) with `.timing = TRUE` and prints ms per step for each module and for the whole step, the garbage collection time, and the heap settings in force. A test runs it and compares the step time, divided by a CPU reference timed in the same process, with a stored baseline, failing above 1.5 times.
- Review: both. The conceptual question is whether a wall-clock test belongs in the suite at all. For now it is skipped on CRAN, on CI and off macOS.

Stacked on #1149, which adds the control this uses. The base is that branch, so the diff shows only this change.

### What it prints

On the laptop (M5 Max), from the source tree:

```
R_VSIZE not set, R_NSIZE not set
10,000 nodes, 100 steps

                 ms.per.step
resim_nets.FUN         11.76
summary_nets.FUN        3.78
infection.FUN           0.86
recovery.FUN            0.18
departures.FUN          0.34
arrivals.FUN            0.14
nwupdate.FUN            2.03
prevalence.FUN          0.29
other                   0.34
step                   19.72

Garbage collection, inside the times above: 0.75 ms per step
CPU reference: 53 ms; step over reference: 0.3736
```

### How stable the guard is

The ratio of step time to CPU reference, one process per sample, on the same laptop:

| Condition | Samples | Step, ms | Ratio |
|---|---|---|---|
| Idle | 8 | 19.4 to 21.5 | 0.388 to 0.423 |
| 6 other processes using a core each | 4 | 21.8 to 23.6 | 0.374 to 0.424 |
| All 18 cores busy | 6 | 26.9 to 30.4 | 0.415 to 0.440 |
| On the slow cores (3.6 times slower) | 5 | 71.6 to 76.3 | 0.395 to 0.461 |

The baseline is 0.40 and the test fails above 0.60. The ratio has only been measured on Apple Silicon, which is why the test skips elsewhere and on CI. Once it has been measured on a Linux node and a CI runner those skips can go.

### Checks

Full suite with the long tests: 4,978 expectations, no failures, with the guard running. Lint is clean. The script needs an EpiModel that has `.timing`; from a source tree it is `Rscript -e 'devtools::load_all(); source("inst/bench/sis-10k.R")'`.

Not here: the 100k EpiModelHIV case, which goes in EpiModelHIV-p, and the base-against-PR identity script.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0834b58fbcac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.