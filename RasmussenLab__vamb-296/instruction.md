# Issue

**Title:** Fix: Update src/create_fasta.py

## Description

In 15638ff, binsplitting was refactored. This change removed the minsize keyword from vambtools.write_bins, which src/create_fasta.py relies on, breaking the script.
Fix this, by making the following changes:
* Read in the FASTA in two passes, one to figure out which sequences to store in memory, and one which stored them
* Filter the bins in the script before calling write_bins
* Change the default max bins from the overly conservative 250 to 1000.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `491590cef90c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.