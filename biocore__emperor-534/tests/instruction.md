# Issue

**Title:** HACK: Add extra attribute to denote text

## Description

THREE.Sprite objects can't properly be rendered when we use the
SVGRenderer, hence we add an extra attribute to the objects we return
from makeLabel. In this attribute text is stored, such that when
rendering we can check for its presence, and add the appropriate SVG
element.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bfc5af083c27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.