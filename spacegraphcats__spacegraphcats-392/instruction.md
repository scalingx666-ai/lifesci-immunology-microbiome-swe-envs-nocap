# Issue

**Title:** [MRG] add documentation and mkdocs site for spacegraphcats

## Description

Website rendering here: http://spacegraphcats.github.io/spacegraphcats/
- [x] add mkdocs github action workflow
- [x] adds mkdocs site navigation file
- [x] adds background and primer on metagenome assembly and assembly graphs, and why one would want to use spacegraphcats
- [x] changes file names of existing doc files so they're ordered (I can change this back if its annoying)
- [x] visualizing BCALM/bandage (#277)
- [x] change build branch to `latest`
- [x] update run guide file output suffixes 
- [x]  spacegraphcats use cases
    - [x] Metagenome bin completion
    - [x] Neighborhood of e.g. horizontally transferred genes
    - [x] Query by hashval
    - [x] multifasta query
    - [x] protein?
    - [x] graphgrep?
- [x] working with spacegraphcats output
- [ ] visualizing the catlas (e.g. like the ecoli graph)
- [x] parameters (k, r)
    - taxonomy results for r=1 vs r = 5 on mock community data (#309)
    - k size graph changes a la bandage supplement
    - CMAG as query

Opportunities to address issues:
- [ ] #354 fix documentation for click interface
- [x] #382 make sure installation docs are up to date
- [x] #313 add link to slides from lab meeting on sgc internals to developer's guide?
- [x] #288 integrating sgc into a snakemake workflow
- [x] #270, #273 read indexing/retrieval

Questions:
- [x] trouble shoot why site url does not resolve...may have to do with `tr_doc`/`latest` branch, but I'm not sure
    - needed to enable docs to render to url in settings :) 
- [ ] should `doc/index.md`, which acts as the landing page for the website, verbatim copy the readme? Right now it only copies a few pieces.
- [x] did `dory_k21_r1/contigs.fa.gz` become `dory_k21_r1/reads.bgz.index`? Because i changed the documentation in `doc/developing-spacegraphcats.md` to say that it did
- [x] is this accurate? `* contigs.sizes - sizes of all cDBG nodes in pickle format; produced by index_cdbg_by_kmer.py`
- [x] should the use cases in `doc/02-spacegraphcats-use-cases.md` have demo code?
    - some do, some don't, we can always add more tutorials later as use cases crystalize.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8ed3249f6a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.