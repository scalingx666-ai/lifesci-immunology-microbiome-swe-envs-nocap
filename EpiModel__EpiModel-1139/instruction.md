# Issue

**Title:** dissolution_coefs(): warn near the departure ceiling and point the error at the duration

## Description

.

With departures, a mean edge duration cannot exceed the ceiling `1 / (1 - (1 - d.rate)^2)`, about `1 / (2 * d.rate)`. The ratio of a duration to the ceiling turns out to be the share of partnership endings that are departures rather than dissolutions, and the adjustment is exactly `coef.adj = coef.crude - log(1 - ratio)`, so it climbs by 2.3 at 90% of the ceiling and by 4.6 at 99%. That is the mechanism behind the table in the issue.

`dissolution_coefs()` now warns for any duration at or above 90% of the ceiling, naming its position in the duration vector and the share:

```
Warning message:
In dissolution_coefs(f, c(60, 30, 950, 100, 1040, 160), d.rate = 0.000478213) :
  duration[3] = 950 (90.8%) and duration[5] = 1040 (99.4%) are at or above 90% of the departure ceiling of 1045.81 for d.rate = 0.000478213 (1 / (2 * d.rate - d.rate^2)). The percentage is the share of partnership endings that are departures rather than dissolutions, and this close to the ceiling coef.adj rises steeply with the duration. Check these durations first; d.rate is the other lever.
```

The error at the ceiling now gives the ceiling and names the duration first, with `d.rate` as the other lever. The `d.rate` bound it states is rounded down so that value does admit the duration:

```
Error in dissolution_coefs(~offset(edges), 60, 0.01) :
  duration = 60 is at or above the departure ceiling of 50.2513 for d.rate = 0.01 (1 / (2 * d.rate - d.rate^2)). At the ceiling departures alone end partnerships faster than the mean duration allows, so no dissolution coefficient can produce it. Lower the duration below the ceiling, or if it is right, lower d.rate below 0.008368.
```

The check runs once over the whole duration vector, so one warning or error lists every stratum, and the two per-branch loops collapse into one vectorized computation. Coefficients are unchanged (tests pin the 2.7.0 values for edges-only, nodematch, and nodemix). A formula with more than two terms now gets the invalid-form error instead of an undefined-object error. The ceiling is documented in `?dissolution_coefs`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56640c3951ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.