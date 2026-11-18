# Issue

**Title:** Add exception handling case when all detected tRNAs are undetermined tRNAs

## Description

Hi George,

I met a KeyError exception when I was annotating INPHARED genomes using Pharokka.
By investigating a detailed case, I found that this exception occurred when all detected tRNAs were undetermined.
In this case, within the create_gff() function, trna_df did not contain the 'anticodon_gb' column, and a KeyError was raised.
In addition, within the create_tbl() function, trna_df did not contain the 'anticodon' column, and a KeyError was also raised.

I've handled it by adding exception handling lines.
Thus, I could be more than happy if you reflect on this solution in your main branch.

Here is an example case
example genome:
```shell
>AJ251789 Lactobacillus casei bacteriophage A2 complete genome.
AACGGTCGGCCTCTTTTTTTCACCCCAAATTGTAACGATTTTTAGGGGATAGGAGGTCAA
TAAGACCCATTTTATATAGATATTAGGAGGTGAAGTGGGAAATGGCTGGAAAATACAAAG
TGTTGCAAATGTCGAAGGGTGATTTGACCAAAGAACGGCAGGAAGCCAAACTACATGCGG
AATTGATGGCCAAAGATGGCATTCCAAAACTTCAGGTGACGCCTCCTAATCATCTTGACC
CAGTCGCAAAACAAGAATACAAGCGAATTATCGAATCTTTGGGGACCTTACCACTTAGAA
ATCTCGATCGCGCCGAGTTGGAAAACTATTGTCATAGGTATTCGGTTTACAAAAACACAT
...
``` 

Error message:
```Python
Traceback (most recent call last):
  File "/..../lib/python3.13/site-packages/pandas/core/indexes/base.py", line 3812, in get_loc
    return self._engine.get_loc(casted_key)
           ~~~~~~~~~~~~~~~~~~~~^^^^^^^^^^^^
  File "pandas/_libs/index.pyx", line 167, in pandas._libs.index.IndexEngine.get_loc
  File "pandas/_libs/index.pyx", line 196, in pandas._libs.index.IndexEngine.get_loc
  File "pandas/_libs/hashtable_class_helper.pxi", line 7088, in pandas._libs.hashtable.PyObjectHashTable.get_item
  File "pandas/_libs/hashtable_class_helper.pxi", line 7096, in pandas._libs.hashtable.PyObjectHashTable.get_item
KeyError: 'anticodon_gb'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/..../miniconda3/envs/phage/bin/pharokka.py", line 494, in <module>
    main()
    ~~~~^^
  File "/..../miniconda3/envs/phage/bin/pharokka.py", line 414, in main
    pharok.create_gff()
    ~~~~~~~~~~~~~~~~~^^
  File "/..../miniconda3/envs/phage/bin/post_processing.py", line 978, in create_gff
    + trna_df["anticodon_gb"].apply(
      ~~~~~~~^^^^^^^^^^^^^^^^
  File "/..../miniconda3/envs/phage/lib/python3.13/site-packages/pandas/core/frame.py", line 4113, in __getitem__
    indexer = self.columns.get_loc(key)
  File "/..../miniconda3/envs/phage/lib/python3.13/site-packages/pandas/core/indexes/base.py", line 3819, in get_loc
    raise KeyError(key) from err
KeyError: 'anticodon_gb'
```  

I've attached an example genome file to reproduce the above error case
[AJ251789.fa.zip](https://github.com/user-attachments/files/22648203/AJ251789.fa.zip)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b2e301276a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.