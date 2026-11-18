# Issue

**Title:** Add continuous integration support

## Description

I've added integration with travis so every time you push to master it will spin up a clean VM and try to install and run the unit tests for RGI.

To finish configuring this you need go and sign into travis via github https://travis-ci.org/
and then enable travis for the RGI repo under your profile https://docs.travis-ci.com/user/getting-started/
Then the SVG 'button' in the README will show the build status of the project.

For some reason the tests are failing with DIAMOND just now, I couldn't easily find the issue so I temporarily switched them to BLAST so they actually run.

Also did some minor typo fixes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `769f5f32b005`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.