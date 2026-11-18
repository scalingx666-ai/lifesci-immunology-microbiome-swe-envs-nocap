# Issue

**Title:** Correct references and add manual references

## Description

I reviewed the HTML after #1002 was merged and found a few reference-related issues to fix.  @rando2 can you please double-check the DOIs I updated in the text?

I also fixed some bad URL references in the vaccines section.  Those failed citations slow down builds.  Some of them should work as-is now that I used `{ }` to escape special characters in the URL.  That's a new pandoc feature.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f2e2387356c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.