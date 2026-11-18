# Issue

**Title:** Fixes minor issues for working with observed network data

## Description

Fixes issues that prevented this EpiModel Gallery example from running:
https://github.com/EpiModel/EpiModel-Gallery/tree/main/2018-08-ObservedNetworkData

* `get_edgelist` stop check no longer uses `dat$param`
* `resim_nets` avoids unnecessary pulls of control settings if `resimulate.network = FALSE`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `331413420039`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.