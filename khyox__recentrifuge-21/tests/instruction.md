# Issue

**Title:** Update kraken.py to support compressed inputs

## Description

The output file of kraken might be very large (hundreds Mb or even larger), so I think it might be useful to support compressed files as input.

A wrapper was added to open compressed/uncompressed kraken output file.
Both gzip and bzip2 format are supported, as well as uncompressed file.

def open_compressed_and_uncompressed(filename):
    ext = os.path.splitext(filename)[1]
    if ext == '.gz':
        import gzip
        return gzip.open(filename, mode='rt')
    elif ext == '.bz2':
        import bz2
        return bz2.open(filename, mode='rt')
    else:
        return open(filename, mode='rt')

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `953ea55a45c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.