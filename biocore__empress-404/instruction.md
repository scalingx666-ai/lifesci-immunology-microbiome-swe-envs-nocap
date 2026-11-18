# Issue

**Title:** Fixes to some small open issues

## Description

- Close #393: document metadata merging complications
- Close #397: remove pep8 requirement
- Close #401: document that Emperor will be reinstalled
- Not an open issue, but adds a border between the header and body when using `qiime tools view` -- see screenshots below

before:
![noborder2](https://user-images.githubusercontent.com/4177727/94746001-acf54200-0330-11eb-8a75-381efeb28232.png)

after:
![border](https://user-images.githubusercontent.com/4177727/94745669-fe510180-032f-11eb-896d-a6c234a0119f.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `864f010d9962`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.