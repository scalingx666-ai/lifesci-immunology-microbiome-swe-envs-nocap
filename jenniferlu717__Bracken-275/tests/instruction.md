# Issue

**Title:** Speed up kmer_distr especially for longer reads

## Description

This pull requests includes the following changes
  * `database.kraken` parser has been rewritten to  reduce memory overhead and slightly faster parsing of integers
  * The kmer classifier has been re-written to reduce redundant work, only consulting the taxonomy tree when needed

In my testing using `631 MB` `database.kraken` generated from a `Krakan 2` database that includes  `protozoa`, `plasmid` and `viral` libraries

Old code
* Read length 50: 1m 45s
* Read length 300: 10m

New code
* Read length 50: 51s
* Read length 300: 1m 20s

I also realized that bracken would sometimes report erroneous taxids (potential overflow?). This has been corrected in this patch as evidenced below.

```
< kraken:taxid|1028729|NW_017607663.1   1028729         -547168256:896 
---
> kraken:taxid|1028729|NW_017607663.1   1028729         0:896 
93965c93965
< kraken:taxid|1028729|NW_017607667.1   1028729         -547174400:471 
---
> kraken:taxid|1028729|NW_017607667.1   1028729         0:471 
93970c93970
< kraken:taxid|1028729|NW_017607672.1   1028729         -528441344:571 
---
> kraken:taxid|1028729|NW_017607672.1   1028729         0:571 
93999c93999
< kraken:taxid|1028729|NW_017607701.1   1028729         -547168256:596 
---
> kraken:taxid|1028729|NW_017607701.1   1028729         0:596 
94001c94001
< kraken:taxid|1028729|NW_017607703.1   1028729         -528433152:1084 
---
> kraken:taxid|1028729|NW_017607703.1   1028729         0:1084 
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8800e4bfd0c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.