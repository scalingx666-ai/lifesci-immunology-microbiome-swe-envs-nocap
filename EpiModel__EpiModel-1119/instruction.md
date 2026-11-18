# Issue

**Title:** Warn when user code needs globals that multisession workers lack

## Description

.

With `ncores > 1`, `netsim()` and `netdx()` run on multisession workers, which start without the global environment or the packages attached in the main session. A module, tracker, updater, `arrivals.FUN`, or formula from a script that uses a global object then fails with "object not found", and an unqualified `lag()` after `library(dplyr)` silently becomes `stats::lag()`.

After Adrien's review this no longer exports anything. Before `future_lapply()`, `netsim()` and `netdx()` scan the user code in their inputs with `globals::globalsOf()` and warn, naming each global object and each function from a package the workers do not attach, by where it is used:

```
Warning: netsim() runs the simulations in separate R sessions, which do not have the global objects or attached packages of this one. Code passed to netsim() uses:
  control$dat.updates: G_RATE
  control$lag.FUN: lag() from dplyr
  control$.tracker.list: helper(), n_distinct() from dplyr
See the Parallel Simulation section of ?netsim.
```

- Formula term names (`edges`, `offset(edges)`) are skipped, so a global named like a term does not trigger it. Term arguments such as `levels = lv` are checked, including in the formation formula held inside a fitted model.
- Sequential and multicore plans share the main session and are not checked.
- The scan takes about 3 ms on a restart from a `netsim` object.
- `globals` is a new import; future already depends on it.

`?netsim` has a new Parallel Simulation section on making the code self-contained: values through `param.net()`, `pkg::fun()` calls, helpers in a package, `trim_env(keep = )` for formulas, or parallelizing outside `netsim()` with `ncores = 1`. The `ncores` docs in `?control.net` and `?netdx` and the `arrivals.FUN` note in `?netclique` point to it.

The tests in `test-netsim-parallel.R` cover the scan directly and with two cores: `netsim()` warns and `ncores = 1` does not, `netdx()` warns and then fails on a global formula argument, and it runs once the formula carries the object with `trim_env()`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `89dde8b6bf07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.