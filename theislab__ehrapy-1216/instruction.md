# Issue

**Title:** filter_observations: criteria on obs without data

## Description

**PR Checklist**

- [x] This comment contains a description of changes (with reason)
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Documentation in `docs` is updated

**Description of changes**

`ep.pp.filter_observations` applies criteria in `query` on `obs` columns also when `X`, or the given `layer`, is `None`. A cohort is often defined by criteria on observation-level fields, such as age or length of stay, before any variables are set up, for instance on an `EHRData` that holds only `.obs`. So far the function failed there while reading the dimensions of the missing array.

```python
edata = ed.EHRData(obs=obs)  # no variables yet
tracker = ep.tl.CohortTracker(edata, columns=["age"])
ep.pp.filter_observations(edata, query=["age >= 18", "sex == 'm'"], tracker=tracker)
```

Criteria on variables, `min_vars`, `max_vars` and `tem_names` need data, and now raise a `ValueError` that says so instead of failing on `None`. `ep.pp.filter_features`, which always needs data, raises the same kind of error.

**Technical details**

- Only the path where the array is `None` changes; with data, `filter_observations` and `filter_features` behave as before.
- `copy=True` returns a filtered copy whose `X` stays `None`, and a `CohortTracker` records every step as usual.

**Tests**

- `test_filter_obs_query_without_data`: obs criteria in place and with `copy=True` on an `EHRData` without `X`, with a tracker.
- `test_filter_obs_without_data_raises` and `test_filter_features_without_data_raises`: the errors for `min_vars`, `max_vars`, `tem_names`, a criterion on a variable, and `filter_features`.
- The six new tests fail without the change; `tests/preprocessing/test_filter.py`: 113 passed, 56 skipped.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13458430000c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.