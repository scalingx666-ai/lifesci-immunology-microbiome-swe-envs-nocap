# Issue

**Title:** change color of msg on profile page

## Description

When changing the user profile, the user gets feedback after he/she hits `Save Edits`. However, this msg is always red, even though it signals success, like here:
![image](https://github.com/qiita-spots/qiita/assets/11960616/6e83bd81-7ce0-41e3-a362-d3d30ceee4c2)

I suggest to use darkgreen by default:
![image](https://github.com/qiita-spots/qiita/assets/11960616/e9c3b98b-f8da-4ce4-9e77-0a1796f60695)
and only change to red (through jinja code in the template) when the msg starts with `ERROR:`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ffd9a069dc6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.