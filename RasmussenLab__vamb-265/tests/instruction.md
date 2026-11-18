# Issue

**Title:** Replace use of Pandas in __main__.py

## Description

There are several reasons not to use Pandas:
* It's a fairly heavyweight dependency, which would be nice to get rid of
* Pandas tend to place loose and fast with the output types and formats, making it much less reliable and stable than ordinary Python code. For example, the column types are autodetected based on the content, and so with the header and the separator. This is because it's designed for interactive "smart" data science. We've already had some bugs due to this.
* DataFrames carries no type information, making the code less readable and maintainable
* Forcing the data into a DataFrame usually inhibits creating more useful types to store the data. For example, it encourages users to encode a tuple of elements as e.g. comma-separated string.

This commit does not remove the use of Pandas in reclustering.py, but it's my plan to eventually completely rewrite the code in that file, then remove it. When that time comes, we can remove Pandas.

Let's give this a go - it might fail due to typing issues.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62baa3582dc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.