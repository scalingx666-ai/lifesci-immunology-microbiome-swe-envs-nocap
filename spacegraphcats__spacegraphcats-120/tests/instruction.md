# Issue

**Title:** update the podar catlas

## Description

Rebuilt the podar catlas and updated the OSF version to podar-2017.05.06b.tar.gz after merge of #118. Much smaller! Faster! Yay!

Merge when ready.

```
% time python -m search.frontier_search data/mircea-sigs/mircea-rm18.0.fa.sig podar 0.1 --purgatory
loaded 5320993 nodes from catlas podar/catlas.csv
loaded query sig Acidobacterium_capsulatum_ATCC_51196
Root containment: 0.627039627039627
Root similarity: 0.015648632926119836
Containment of frontier: 0.627039627039627
Similarity of frontier: 0.6241299303944315
Size of frontier: 420384 of 5320993 (7.9%)
Overhead of frontier: 0.007380073800738007
Number of leaves in the frontier: 4
Number of empty catlas nodes in the frontier: 420112
Size of the shadow: 1232621
       41.58 real        36.61 user         1.96 sys
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8d3fb7561cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.