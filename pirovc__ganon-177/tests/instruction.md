# Issue

**Title:** Feature/ganon core io

## Description

Change ganon on c++ side to work with minimal input. Now, the LCA file is not written by default and the report file (rep) is the default output.

*ganon-build*

default input:
- fasta file(s) 

optional input:
- seqid start end binid (if not provided build ibf with one file per bin)

output:
- ibf
    
*ganon-classify*

default input:
- ibf
- fastq file(s)

optional input:
- map (target binid)
- tax (node/target parent [rank] [name])

default output:
- rep (no map ->output binid as target. no tax -> no lca)

optional output:
- lca
- all
- unc

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9921af11e920`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.