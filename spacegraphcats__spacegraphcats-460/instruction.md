# Issue

**Title:** [MRG] Remove kmer size argument from `rule build_multifasta_index` in spacegraphcats/conf/Snakefile

## Description

This PR removes the argument ksize from `rule build_multifasta_index`, which uses the script `search.index_cdbg_by_multifasta.py`. In the script, ksize is inferred from the cdbg, not a user-specified argument

```
    ksize = kmer_idx.ksize
    notify(f"Using ksize {ksize} from k-mer index.")
    notify("loaded {} k-mers in index ({:.1f}s)",
           len(kmer_idx), time.time() - ki_start)
```

ready for review and merge after checks pass

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `080a43c0a8e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.