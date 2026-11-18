# Issue

**Title:** stat calc updates

## Description

stacked on #705





combines `make_formation_table` and `make_dissolution_stats` into `make_stats_table`

parallelizes ESS calculation in `netdx`

extends `get_nwstats` to allow for returning a list of stats matrices

simplifies some backend logic

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48602311a91d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.