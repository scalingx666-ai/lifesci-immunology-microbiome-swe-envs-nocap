# Issue

**Title:** Allow for creation of empty FCS files

## Description

Hey,

Thank you for providing this lightweight tool. I have some use-cases where I need to perform filtering on an FCS file, which can result in an empty `event_data` array. Typically, this would raise a `ValueError`. However, by removing a couple of lines, I can still write the file to disk while retaining the metadata. Maybe you could drop this as I haven't noticed any problems with the created files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b92672357fa4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.