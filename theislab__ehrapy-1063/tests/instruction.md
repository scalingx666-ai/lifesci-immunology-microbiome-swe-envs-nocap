# Issue

**Title:** address pandas futurewarning

## Description

**PR Checklist**

- [x] This comment contains a description of changes (with reason)
- [x] Referenced issue is linked
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] Documentation in `docs` is updated

**Description of changes**

 pandas `FutureWarnings` in the tests. Affected files

- `ehrapy/plot/_variable_correlation_plot.py`: Updated  `.stack()` calls to use `future_stack=True` (the new default in pandas 3.0) and removed `dropna=False`, which is not accepted when `future_stack=True`.
- `ehrapy/plot/_sankey.py`: Added `observed=True` to a `groupby` call on obs columns
- `ehrapy/preprocessing/_bias.py`: `observed=True` again

**Technical details**

`stack`: pandas 2.1 introduced a new implementation of `DataFrame.stack()` that will become the only version in 3.0. The key behavioural difference is that the new implementation never introduces spurious `NaN` values, so `dropna=False` is no longer needed. The output for our use cases is identical.

`groupby(observed=True)`: The pandas default for `observed` on categorical columns changes from `False` to `True` in pandas 3.0. With `observed=False`, all possible category combinations appear in the result even with zero counts. For our use cases here this is incorrect behaviour: zero count category pairs in the bias analysis would result in `0/0 = NaN` ratios. In a sankey diagram a zero count flow makes no sense as well, so in both cases I set `observed=True`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2fc269d2a5d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.