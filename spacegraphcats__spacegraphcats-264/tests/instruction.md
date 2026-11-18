# Issue

**Title:** add the catlas name to the output signature name

## Description

After running 
```
% make dory-test
% sourmash sig describe dory_k21_r1_search_oh0/*.sig
```
we now see:
```
...
signature filename: dory_k21_r1_search_oh0//dory-head.fa.contigs.sig
signature: nbhd:TRINITY_DN290219_c0_g1_i1 len=854 path=[1764:0-36 1765:37-60 1767:61-545 1762:546-569 1763:570-853] [-1, 1764, 1765, 1767, 1762, 1763, -2] from dory_k21_r1
...
signature: nbhd:nomatch from dory_k21_r1
source file: random-query-nomatch.fa.contigs.sig
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3362367dfb8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.