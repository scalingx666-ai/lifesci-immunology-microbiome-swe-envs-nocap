# Issue

**Title:** fix(setup.py): use ~= to constrain major version

## Description

package ~= x.y.z is the same as (package >= x.y.z, package == x.*). This prevents the wrong numpy version (2.x) from being installed, such as in #467 (which is not yet properly fixed and should NOT have been closed).

See: https://peps.python.org/pep-0440/#compatible-release

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0da1160fdf53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.