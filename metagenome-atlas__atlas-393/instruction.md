# Issue

**Title:** Don't checksum for EggnogDB

## Description

This should fix #391 
@johanneswerner

I will need to test it first locally if this works. I think there is also an option to run eggNOG mapper with mmseqs. 
@Sofie8 Do you know the commands that should be changed in the [code](https://github.com/metagenome-atlas/atlas/blob/master/atlas/rules/genecatalog.snakefile#L419)? 
If you want you can follow the steps of installing atlas in dev mode and try it out yourself-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bfbfb1746b83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.