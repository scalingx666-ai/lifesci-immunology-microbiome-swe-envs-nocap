# Issue

**Title:** feat: CONSORT-style branching for CohortTracker

## Description

.

`CohortTracker.__call__` gains a `parent=` kwarg (label or index, defaults to the previous step), and `plot_flowchart` now renders an interactive HoloViews/Bokeh overlay so branched trees draw cleanly.

```python
ct = ep.tl.CohortTracker(edata, columns=["gender", "race", "age"])
ct(edata, label="Screened")
ct(enrolled, label="Enrolled", operations_done="met eligibility")
ct(arm_a, label="Arm A", operations_done="randomized", parent="Enrolled")
ct(arm_b, label="Arm B", operations_done="randomized", parent="Enrolled")
ct(arm_a_followup, label="Arm A 12-mo", operations_done="completed", parent="Arm A")
ct(arm_b_followup, label="Arm B 12-mo", operations_done="completed", parent="Arm B")
ct.plot_flowchart(title="CONSORT")
```

**Before** (linear-only, old API)

![before](https://raw.githubusercontent.com/theislab/ehrapy/pr-assets/cohort-branching/before.png)

**After** (branching, new API)

![after](https://raw.githubusercontent.com/theislab/ehrapy/pr-assets/cohort-branching/after.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `87cb40850015`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.