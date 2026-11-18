# Issue

**Title:** use available processor for process not all on host

## Description

Hello 

this PR fix probelem mentionned in 

some sample output of megahit in taskset environnement once applied

```
maestro-builder:megahit/test_data > megahit -t 12 -1 r3_1.fa  -2 r3_2.fa -o out 2>&1| grep  -e cpu -e thread 
2023-01-26 18:21:10 - Start assembly. Number of CPU threads 12 

```

now run with 8 core constrain (using taskset)

```
maestro-builder:megahit/test_data > taskset -c 1-8 megahit -t 12 -1 r3_1.fa  -2 r3_2.fa -o out2 2>&1| grep  -e cpu -e thread
2023-01-26 18:21:47 - Maximum number of available CPU thread is 8.
2023-01-26 18:21:47 - Number of thread is reset to the 8.
2023-01-26 18:21:47 - Start assembly. Number of CPU threads 8 
```
no diff in the results
```
maestro-builder:megahit/test_data > diff -q out/final.contigs.fa out2/final.contigs.fa 
maestro-builder:megahit/test_data > echo $?
0
```

regards

Eric

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `769cfa23faa4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.