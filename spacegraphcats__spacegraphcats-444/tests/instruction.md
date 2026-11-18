# Issue

**Title:** [MRG] add translated catlas annotation functionality w/multifasta approach

## Description

Note: this is a PR into #379, although it doesn't really need to be.

.

This PR extends the multifasta indexing/annotation capabilities added in  with protein queries. Briefly, it:
* adds a new script `spacegraphcats/search/index_cdbg_by_multifasta_x.py` that does protein-space search of the cDBG + expansion to neighborhoods;
* adds three new config parameters, `multifasta_x_reference`, `multifasta_x_protein_ksize`, and `multifasta_x_query_is_dna`.
* adds two new concrete targets in the Snakefile, `build_multifasta_x_index` and `build_cdbg_list_by_record_x`;
* the target `build_cdbg_list_by_record_x`  produces a file `{catlas_dir}_multifasta_x/multifasta_x.cdbg_annot.csv` that contains the nice mappings between neighborhoods and protein annotations;
* adds tests and docstrings;

As with protein query of the catlas #379, this PR cannot use the pre-built k-mer index to search the cDBGs. So, it does an iterative search of all the unitigs, which might take a while for large catlases. See some of the benchmark times, below.

TODO:
- [x] fix/retain filenames for each record
- [x] add config options into Snakefile, etc.
- [x] figure out how to produce `multifasta.cdbg_annot.csv`
- [x] testing, robustness, etc.
- [x] evaluate speed, functionality on a bigger catlas than dory...
- [x] add docstrings to top of multifasta scripts

## Example

To annotate the twofoo cDBG with a ~dozen genes, run:

```
python -m spacegraphcats run twofoo build_cdbg_list_by_record_x
```
and you'll get output like so:
```
...
saved 11 query names with cDBG node mappings (of 11 queries total)
saved 355 cDBG IDs (of 206855 total; 0.2%) with at least one query match
```
(This only takes 35 seconds or so, which is pretty good!)

## A larger query: time

I downloaded a full _Shewanella baltica_ proteome, GCF_001620325.1_ASM162032v1_protein.faa.gz, which has almost 4300 proteins in it, and ran this code.

Results:
```
...
saved 3769 query names with cDBG node mappings (of 4255 queries total)
saved 155286 cDBG IDs (of 206855 total; 75.1%) with at least one query match
```
and time:
```
real    0m43.729s
user    0m37.468s
sys     0m2.704s
```
so, that's pretty fast!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `567ed21deed5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.