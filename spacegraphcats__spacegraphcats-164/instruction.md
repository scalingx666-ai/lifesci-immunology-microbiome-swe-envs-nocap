# Issue

**Title:** [MRG] Add 'search.catlas_info' to display some basic stats about catlases.

## Description

Example output:

```
% python -m search.catlas_info twofoo -k 31
loaded 26041 nodes and 11 layers from catlas twofoo/catlas.csv
top catlas node 26040 has 1271 children.
8523 layer 0 catlas nodes, corresponding to 335388 cDBG nodes.
top node minhash has 10165 mins, k=31 scaled=1000
 => ~1.0165e+07 31-mers total.
581 empty child nodes (of 1271) beneath top node
```

I think some additional useful output might be:

* shadow size of each of the (top_level-1) nodes
* component size distribution (should be approximated by above, no?)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fd7be11d07d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.