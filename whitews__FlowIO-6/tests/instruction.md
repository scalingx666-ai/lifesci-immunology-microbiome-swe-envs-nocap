# Issue

**Title:** Fix issue #5

## Description

This pull request provides one test case for issue #5  and applies a fix.

First commit: 

> This commit introduces a test which exposes a bug in
> FlowData.write_fcs, which means that channels are given the wrong
> index in the file created by write_fcs, if there are more than 9
> channels.
> 
> The issue is caused by the use of the sorted function in write_fcs to
> sort the keys of the channel dictionary. This results in a
> lexicographical ordering since the dictionary keys are strings (not
> integers).

Second commit:

> The mapping of channel index to channels are now preserved by
> write_fcs.
> 
> Small bug in the test case from previous commit, where PNS name is not
> correctly written by create_fcs. Don't know how to fix but pretty
> confident not related to write_fcs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a17c43d6ba1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.