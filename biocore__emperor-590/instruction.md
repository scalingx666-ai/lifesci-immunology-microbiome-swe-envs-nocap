# Issue

**Title:** BUG/BLD: Fix problem with labels being clipped

## Description

Reported by @ebolyen, long axes labels would be clipped. To fix this
I've made the font canvas bigger, so that it can at least fit 25
characters, after which it will add `...` at the end of the label (this
logic was already in place but was not noticeable due to the bug).

I've also upped the JINJA2 version to at least be 2.9.
see

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8eef0b5f68dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.