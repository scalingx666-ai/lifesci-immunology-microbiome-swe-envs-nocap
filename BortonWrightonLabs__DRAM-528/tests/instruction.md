# Issue

**Title:** fix: email flag fix to send emails on run complete

## Description

The email flag was silently failing for a few reasons. Inocrrect paths to assets, not passing the header, and not giving feedback on sendmail result. The plaintext email also failed because of not sending the header properly. Now it tries sendmail for the html email, if that fails, it uses the plaintext email as a backup and lets you know this in the console output and in log.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `032d408112c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.