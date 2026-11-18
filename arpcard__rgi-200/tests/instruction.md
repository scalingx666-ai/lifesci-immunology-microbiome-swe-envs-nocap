# Issue

**Title:** Use Pyrodigal instead of Prodigal for ORF prediction

## Description

Hi @raphenya ! 

This PR proposes to replace Prodigal with Pyrodigal for running the ORF prediction stage. Pyrodigal is a Python library binding to Prodigal with additional performance enhancements. I'm the author of Pyrodigal, so ofc this is not a completely neutral list, but there are several advantages over Prodigal that I'll try to list down:

## Single-threaded speed

Pyrodigal comes with a SIMD pre-filter to skip score computation for invalid gene pairs. This typically saves around half of the runtime for processing a genome in single mode (and more than that in metagenomic mode) on platforms with supported CPU features (SSE or NEON). I did a small writeup about this in the [paper](https://joss.theoj.org/papers/10.21105/joss.04296).

I ran some benchmarks on a single closed genome ([NC_004129](https://www.ncbi.nlm.nih.gov/nuccore/NC_004129)) to compare the runtime (still using BLAST for the downstream analysis):

Mode | RGI w/ Prodigal | RGI w/ Pyrodigal | 
----|-----|-----
Default| 245s | 205s |
Low quality | 340s | 272s |

## Multi-threading

Pyrodigal supports re-entrant multithreading, so you can use multi-threaded ORF prediction even when running in single mode, contrary to what the code is currently doing with Prodigal where you only run multi-threaded prediction in `--low_quality` mode. This improves the runtime even more on fragmented genomes (e.g. [548.SAMN21245456](https://www.ncbi.nlm.nih.gov/biosample/?term=SAMN21245456)):

Mode | RGI w/ Prodigal | RGI w/ Pyrodigal | 
----|-----|-----
Default| 231s | 153s |
Low quality | 241s | 165s |

 ## Simpler installation

Contrary to Prodigal, Pyrodigal can be `pip install`ed, so it's one less dependency to worry about for people who don't use conda. Otherwise it's also in Bioconda.

## Same results

Despite the faster speed, Pyrodigal and Prodigal produce exactly[^1] the same output.

[^1]: Well, almost. During the refactor I found a bug in Prodigal that got all genes on the reverse strand to be penalized. It was fixed  but Prodigal never got a new release, so unless you recompile the code yourself you're still getting a buggy version. On the contrary, Pyrodigal contains the fix. So the "recompiled/fixed" Prodigal and Pyrodigal predict exactly the same thing (this is tested for), but the buggy Prodigal and Pyrodigal may occasionally diverge.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8031848eeaee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.