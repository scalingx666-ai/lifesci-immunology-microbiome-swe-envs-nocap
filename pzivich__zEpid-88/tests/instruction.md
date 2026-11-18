# Issue

**Title:** refactor spline so an anonymous function can be returned for use elsewhere

## Description

Previously my code might look like:
```python
rossi_with_splines[['age0', 'age1']] = spline(rossi_with_splines, var='age', term=2, restricted=True)
cph = CoxPHFitter().fit(rossi_with_splines.drop('age', axis=1), 'week', 'arrest')

# this part is nasty
df =rossi_with_splines.drop_duplicates('age').sort_values('age')[['age', 'age0', 'age1']].set_index('age')
(df * cph.hazards_[['age0', 'age1']].values).sum(1).plot()
```

vs 

```python
spline_transform, _ = create_spline_transform(df['age'], term=2, restricted=True)
rossi_with_splines[['age0', 'age1']] = spline_transform(rossi_with_splines['age'])

cph = CoxPHFitter().fit(rossi_with_splines.drop('age', axis=1), 'week', 'arrest')

ages_to_consider = np.arange(20, 45))
y = spline_transform(ages_to_consider).dot(cph.hazards_[['age0', 'age1']].values)
plot(ages_to_consider, y)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf8ff035f72e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.