# Issue

**Title:** Error message clarification for soft-split trial on compressed database

## Description

## Issue reported



## Summary

When compressed target database with long sequence exceeding `--max-seq-len` passed to the soft-split logics, an error captured from `DBReader.cpp`, but actual cause is under `splitsequence.cpp`.

There is no way that user would know what should be changed to workaround.

## Changes

- Condition check added on `splitsequence.cpp` to print proper error messages and to quit early.
- Workaround options added on error messages.

## Validation

### Create fastas for tests
```
awk 'BEGIN {
    print ">query"
    for (i = 0; i < 200; i++) printf substr("ACGT", i % 4 + 1, 1)
    print ""
}' > query.fa

awk 'BEGIN {
    print ">long_target"
    for (i = 0; i < 12050; i++) printf substr("ACGT", i % 4 + 1, 1)
    print ""
}' > target.fa
```

### Build databases for tests
```
mmseqs createdb query.fa queryDB --compressed 0
mmseqs createdb target.fa target_uncompressed --compressed 0
mmseqs createdb target.fa target_compressed   --compressed 1
```

### Run the tests
```
# Test1: Should work fine
mmseqs search \
    queryDB target_uncompressed result_uncompressed tmp_uncompressed \
    --search-type 3 \
    --max-seq-len 10000 \
    --sequence-overlap 0 \
    --sequence-split-mode 1 \
    --mask 0 \
    --threads 1 \
    -v 3

# Test2: Should cause the error reported
mmseqs search \
    queryDB target_compressed result_compressed tmp_compressed \
    --search-type 3 \
    --max-seq-len 10000 \
    --sequence-overlap 0 \
    --sequence-split-mode 1 \
    --mask 0 \
    --threads 1 \
    -v 3

# Test3: Should work fine - used hard-split over Test2
mmseqs search \
    queryDB target_compressed result_hard_compressed tmp_hard_compressed \
    --search-type 3 \
    --max-seq-len 10000 \
    --sequence-overlap 0 \
    --sequence-split-mode 0 \
    --compressed 1 \
    --mask 0 \
    --threads 1 \
    -v 3
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d401e78c2d18`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.