# Issue

**Title:** Fix infected-count comparison in crosscheck.net()

## Description

From the v2.6.2 release review.

`crosscheck.net()` counted infected nodes on the initial network with `status == 1`. Built-in network statuses are the character codes `"s"`, `"i"`, and `"r"`, which the `statOnNw` guard directly above this check already requires, so the comparison never matched and the count was always 0.

The effect is the opposite of a missed warning. Because the count was always 0, the mismatch test reduced to `i.num != 0`, so the warning fired on every model that supplied both a `status` vertex attribute and a nonzero `i.num`, including models where the two agreed exactly. It is raised with `immediate. = TRUE`, so users saw it on every run.

Observed behavior, network with 10 infected nodes:

| case | before | after |
|---|---|---|
| `i.num = 10` (matches) | warns | silent |
| `i.num = 50` (mismatch) | warns | warns |

The `i.num = 50` case was reaching the right outcome for the wrong reason, and the `i.num = 10` case was a false positive on correctly specified models.

Fixed by comparing against `"i"`. Also unwrapped the warning string, which carried an embedded newline and source indentation into the rendered message.

Tests cover matching and mismatching counts, a network with no infected nodes, and a two-group model where the network total is compared against `i.num + i.num.g2`. Confirmed the two matching-case assertions fail against the unfixed code, so they are not vacuous.

Checks:

- `NOT_CRAN=true` full suite: 3098 passing, 0 failures, 0 skips.
- `R CMD check --as-cran --no-manual`: 0 errors, 0 warnings; tests and examples OK. The 2 NOTEs are pre-existing on `main` and fixed by #1055 (dead NEWS URLs plus stale `Date`, and the review doc at top level).
- `lintr`: 0 findings.

Branched from `main`, independent of #1054, #1055, and #1056.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ef97195118f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.