# Issue

**Title:** Fix the forbidden symbols when using unpackdb

## Description

fix issue #466



> <>:"/ | ?* is not allowed in file path of Windows(all) and Linux(only /) when created separated database files with sequence names. Therefore, these symbols should be substituted with others.

> At file src/util/unpack.cpp, substitute these forbidden symbols with others.
As '|' is frequently appeared in sequence name as:
`A0A348AT68|unreviewed|Fluorescent`
We change '|' to '!':
`A0A348AT68!unreviewed!Fluorescent`
Other symbols are changed to '@':
`W5UC41|unreviewed|Nidogen-1|taxID/7998`->`W5UC41!unreviewed!Nidogen-1!taxID@7998`

Then everything is ok!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `488df8634ebd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.