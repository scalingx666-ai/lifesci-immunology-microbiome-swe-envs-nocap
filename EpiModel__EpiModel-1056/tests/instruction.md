# Issue

**Title:** Fix two parameter-table name-checking edge cases

## Description

Item 5 of the v2.6.2 release review. Both defects are in `check_params_names()`, which every parameter-table path runs through: `param.net_to_table()`, `param.net_from_table()`, `create_scenario_list()`, and `param.random.set` sampling.

**Vector positions containing a zero.** The suffix was matched with `(_[1-9]+)?`. That bracket expression excludes `0` at every position, not just the first, so the failure is not simply "10 or higher":

| name | before | after |
|---|---|---|
| `x_9` | ok | ok |
| `x_10` | malformed | ok |
| `x_11` | ok | ok |
| `x_20` | malformed | ok |
| `x_99` | ok | ok |
| `x_100` | malformed | ok |
| `x_0` | malformed | malformed |
| `x_01` | malformed | malformed |

So `param.net_to_table(param.net(x = 1:10))` failed, but `x = 1:9` and a hypothetical vector indexed only 11 to 19 were fine. Widened to `(_[1-9][0-9]*)?`, which keeps rejecting zero and leading-zero positions.

**Reserved names with a position suffix.** The guard matched exactly, so a table containing `random.params_1` and `random.params_2` passed, and `unflatten_params()` then rebuilt a forbidden `random.params` element holding numeric values where generator functions are expected. The guard now strips the position suffix before comparing, and reports the offending entries as the user wrote them rather than the stripped base name.

Dot-prefixed internals like `.param.updater.list` are unaffected either way: they are rejected earlier by the format check, since a flat parameter name must begin with a letter. The tests assert that explicitly so the two guards do not get conflated later.

Tests added for round-tripping 10, 12, and 100 element vectors across numeric and character types, zero and leading-zero rejection, names that merely end in digits (`beta2`, `paramSet10`), scalar and suffixed reserved names through both the table and scenario paths, and names that merely share a reserved prefix (`random.params.mine`).

Checks:

- `NOT_CRAN=true` full suite: 3114 passing, 0 failures, 0 skips (3096 before, 18 new assertions).
- `R CMD check --as-cran --no-manual`: 0 errors, 0 warnings. The 3 NOTEs are all pre-existing on `main` and fixed by #1055 (two dead NEWS URLs, stale `Date`, review doc at top level); none relate to this change.
- `lintr`: 0 findings.

Depends on nothing; branched from `main` and independent of #1054 and #1055.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67c91211dd73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.