# Issue

**Title:** Resolve bin name clashes between Z and Y space in AAE

## Description

The AVAMB ensemble model produces bins from the Z space, the Y space and the ordinary VAE model. When the FASTA bins are written with the --minfasta flag, the bins derived from the three models would erroneously  overwrite each other.

Now, the written bins may be given an optional prefix to avoid name clashes. This prefix is only used when writing bins from the AAE Z and Y spaces - the VAE and VAEVAE models use no prefix.

So, now the bins created using the --minfasta flag with the AAE model will be called e.g. `z_S5C9` or `y_S12C51402`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77e1cba32a3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.