# Issue

**Title:** Add new methods to render individual Emperor components

## Description

Adding 4 new methods that will make integration with Empress much more straightforward. Before we were stripping the formatted HTML based on line numbers. Now CSS, HTML and JS blocks can be individually rendered via dedicated methods. In addition, custom code can be added via the `js_on_ready` attribute.

I updated the documentation to reflect these changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `151a6b9a79fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.