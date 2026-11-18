# Issue

**Title:** Elegant display of stored db descriptions

## Description

This makes the `anvi-pan-graph-display` to be able to display descriptions stored in the database in a nice way.

When there is a default state in the db (which always is the case for pan-graph-db files) as well as a description stored in it (via `anvi-update-db-description`), anvi'o simply draws the display, hides the setting panel, and show the description window, leaving its user with a display like this:

<img width="2008" height="1201" alt="image" src="https://github.com/user-attachments/assets/23b02f0b-5349-431d-845b-7a685ddcd9fe" />

Rather than a blank window and a Draw button waiting to be pressed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a684860b2f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.