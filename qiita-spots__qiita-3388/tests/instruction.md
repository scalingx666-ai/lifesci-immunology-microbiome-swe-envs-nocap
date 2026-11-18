# Issue

**Title:** Config statsmap lat long

## Description

It would be nice, if the Stats world map view could be centered by the user, e.g. I'd like to showcase European samples:
![image](https://github.com/qiita-spots/qiita/assets/11960616/baa7cc04-26fb-4878-ba6e-ebbf0bb48ef8)
Therefore, I suggest to have latitude and longitude as parameters in Qiita's configuration file. I thought the portal section might be appropriate, because different portals also might want to show different locations?
The defaults are Boulder, CO, i.e. if a user gives the parameters without values or skips these parameters altogether

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `667a22a7566f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.