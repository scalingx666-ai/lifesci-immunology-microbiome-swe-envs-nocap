# Issue

**Title:** Document a few dependencies more clearly in the README, and also work on fixing the build

## Description

This PR adds an "installation troubleshooting" section to the README; this addresses #550 and #553. It also adds two short places indicating where users can get support (opening an issue / via the Q2 forum).

**Update:** Multiple tests in the build are failing due to changes in the dependencies' behavior:

1. One of the failures is due to `biom-format` now explicitly raising errors when `Table.update_ids()` is called with a dict containing non-string values (as done in [this test](https://github.com/biocore/empress/blob/bf6f755c5187e543ff13c2c624b153fb97918b23/tests/python/test_tools.py#L143-L145)). This PR fixes this test. I've also submitted  to `biom-format` which clarifies this behavior.

2. Another issue (causing two failing tests) is due to our use of "linear" trees causing problems with iow. This time, the problem is not on our side but on iow's, and I contend that we should keep the linear trees in the tests (if only to make sure that these sort of trees remain explicitly supported). I have submitted  to iow which fixes the relevant problem.

Even though this build is currently failing, I imagine that it's probably better to merge this PR in sooner rather than later (I'm aware this is me being a hypocrite considering the backlog of things I need to review, sorry...) -- having the installation documentation up-to-date will prevent user confusion.

Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf6f755c5187`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.