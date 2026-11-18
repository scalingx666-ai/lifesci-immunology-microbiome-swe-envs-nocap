# Issue

**Title:** collapse ref section by def, load scite badges on intersect

## Description

- allows the accordion plugin to accept default collapsed state for each heading \*
- only adds scite badge when citation comes into view
- make attributes plugin run on `DOMContentLoaded` (after page text and dom parsed but before scripts/styles/images/external resources load) instead of `load` (after everything is finished loading), to make sure it runs before other plugins \*
- cleans up a few lines (left-in console.logs, script type="module", etc) \*

\* changes we probably want to make upstream in rootstock

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3fd31503074`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.