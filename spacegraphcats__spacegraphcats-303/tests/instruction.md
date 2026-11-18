# Issue

**Title:** [MRG] add dominator abundance counting, per sample.

## Description

This PR adds graph and dominator abundance counting: given a catlas and a sample, calculate the abundances of the cDBG nodes and catlas domset in the sample, using k-mers.

One use for this is when you have a catlas built from multiple samples, and you want to output expression directly on the domset using abundances from individual samples. This then could then be used to do differential expression analysis with e.g. corncob.

Usage:
```
python -m spacegraphcats.search.count_dominator_abundance twofoo_k31/ twofoo_k31_r1/ data/2.fa.gz data/63.fa.gz
```

This will create four files, `twofoo_k31_r1_abund/{2,63}.fa.gz.cdbg_abund.csv` and `twofoo_k31_r1_abund/{2,63}.fa.gz.dom_abund.csv`. The `cdbg_abund.csv` files contain the columns `cdbg_id,abund,node_size`, and the `dom_abund.csv` files contain the columns `dom_id,level,abund,size`. Here `abund` is the abundance calculated from the sample given , while `size` is the total number of distinct k-mers beneath that node.

The output directory can be overridden with `--outdir`, and the prefix of the output files can be overridden with `--prefix`.

TODO:
- [x] add some minimal tests!
- [x] update documentation at top
- [x] consider moving scripts under spacegraphcats/ package

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `976022994dab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.