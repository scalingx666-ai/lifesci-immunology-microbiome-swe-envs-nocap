# Issue

**Title:** [MRG] provide a nicer error message when bcalm fails to run

## Description

Fixes  thx @charlesreid1!

Output is now:
```
...
(bbcalm -in bcalm.dory.k21.inputlist.txt -out dory/bcalm.dory.k21 -kmer-size 21 
-abundance-min 1 >& dory/bcalm.dory.k21.unitigs.fa.log.txt && rm -f dory/bcalm.d
ory.k21.{h5,unitigs.fa.glue*}) || printf '**\n**\n** Cannot run BCALM 2! Please 
install it and make sure it is on your path!\n**\n**\n'
**
**
** Cannot run BCALM 2! Please install it and make sure it is on your path!
**
**
Waiting at most 3 seconds for missing files.
...
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4ba1112e8dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.