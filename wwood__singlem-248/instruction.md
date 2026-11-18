# Issue

**Title:** Docs

## Description

Just added the long-read stuff to both README.md files. Version is just my best guess.
Didn't bother changing the methods because they didn't mention short reads, let me know if you'd want it explicitly stated there.

Extra changes while I was here:
Added badges for different install methods to make it easier for people to do so from the main GitHub page.
Changed the name of the test-singlem.yml workflow to make the badge for current build status nicer (badge text will update once merge passes the tests).
Added 2 lines at the top emphasising the recent upgrades.
These extra changes are only in the main README.md, not the docs/README.md.

Also saw the codex pull request, so replaced the references to --genome-fasta-files that it missed in the docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6959b5dedb39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.