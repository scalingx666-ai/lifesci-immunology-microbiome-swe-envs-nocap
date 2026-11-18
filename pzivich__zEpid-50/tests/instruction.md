# Issue

**Title:** improving _plotter function to use errorbars and kwargs better

## Description

This PR refactors `_plotter` to use errorbars and sets defaults. I think this is the abstraction you want. 

Using your test code: 
```python
import matplotlib.pyplot as plt
import zepid as ze

df = ze.load_sample_data(False)

rd = ze.RiskDifference()
rd.fit(df, exposure='art', outcome='dead')

rd.plot(marker='*', markersize=20, color='r')  # Custom markers
plt.show()
```

we get nice pictures:
![screen shot 2018-12-17 at 1 23 45 pm](https://user-images.githubusercontent.com/884032/50106999-612ae480-01ff-11e9-82d9-69fd4f3b0445.png)


I've also confirmed this works for >2 groups.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59adceca4b3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.