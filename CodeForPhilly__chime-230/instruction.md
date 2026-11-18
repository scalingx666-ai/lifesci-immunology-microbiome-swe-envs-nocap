# Issue

**Title:** Presentation text usability

## Description

This PR includes some quick fixes to make it more obvious that users can immediately use it for their location (and don't need to deploy their own unless really want to).

- Tweak mentions of Penn Medicine
- Add some intro text
- Moves Slack & Github links to a header section (at least one reviewer should build & visually check this locally — I did not)

TODO/Wishlist, not in this PR:
- Right-align the header (containing the new links) so it feels more like a navigation bar.
- Align the app title next to the Penn Medicine logo

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7691f5f26801`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.