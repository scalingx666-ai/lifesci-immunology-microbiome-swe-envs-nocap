# Issue

**Title:** Fix multiple validation jobs

## Description

Addressing #3379: 
With the proposed changes, both validation jobs of a deblur command successfully run through in my local setup. I suspect two mistakes of the current code:
1. maybe a copy&paste error of lines 1108ff as they seem to be identical to 1091ff
https://github.com/qiita-spots/qiita/blob/5ab3ebbca79e66441f2df2b73d879ec136450048/qiita_db/processing_job.py#L1091-L1114
2. even though the dependent jobs where "submitted" as child processes, they were not "registered" by Qiita's DB, such that Qiita did not "poll" for successful execution and thus could never set status to "success" of these job(s) even though the actual process did run through and finished with exit 0

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d49339f9f973`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.