# Issue

**Title:** Explicitly load underscore.js and bump version strings

## Description

ScenePlotView wasn't explicitly loading underscore.js, so this
dependency was loaded from whatever was already available in the
environment, specifically when a plot was loaded in the notebook Emperor
would load underscore.js from that env.  In recent versions of Jupyter
they moved from underscore.js to lodash.js, and while the two libraries
are compatible, they are not 100% compatible, namely _.any is no longer
defined.

Seems like this problem is only restricted to Jupyter notebook renders,
from testing in view.qiime2.org, and standalone plots everything looks
fine.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6df010ce08c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.