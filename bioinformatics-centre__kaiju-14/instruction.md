# Issue

**Title:** make makeDB.sh more readable

## Description

`-n` and `-e` are options of `echo`, so the they are missing in the help message.

Before:

```shell
$ ./makeDB.sh 
Error: Use one of the options -r, -p, -n pr -e

This program creates a protein reference database and index for Kaiju.
Several source databases can be used and one of these options must be set:

-r all complete bacterial and archaeal genomes in the NCBI RefSeq database

-p all proteins belonging to the set of representative genomes
from the proGenomes database

NCBI BLAST non-redundant protein database "nr":only Archaea, bacteria, and viruses

NCBI BLAST non-redundant protein database "nr":
like -n, but additionally including fungi and microbial eukaryotes

Additional options:
-v additionally add viral genomes from RefSeq,
when using the RefSeq or proGenomes database

-t X set number of parallel threads for index construction to X (default:5)
The more threads are used, the higher the memory requirement becomes.

--noDL do not download files, but use the existing files in the folder.

```


After:

```shell
$ ./makeDB.sh 
Error: Use one of the options -r, -p, -n or -e

This program creates a protein reference database and index for Kaiju.
Several source databases can be used and one of these options must be set:

  -r all complete bacterial and archaeal genomes in the NCBI RefSeq database

  -p all proteins belonging to the set of representative genomes
     from the proGenomes database

  -n NCBI BLAST non-redundant protein database "nr":
     only Archaea, bacteria, and viruses

  -e NCBI BLAST non-redundant protein database "nr":
     like -n, but additionally including fungi and microbial eukaryotes

Additional options:

  -v additionally add viral genomes from RefSeq,
     when using the RefSeq or proGenomes database

  -t X set number of parallel threads for index construction to X (default:5)
     The more threads are used, the higher the memory requirement becomes.

  --noDL do not download files, but use the existing files in the folder.

```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d15f622e3898`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.