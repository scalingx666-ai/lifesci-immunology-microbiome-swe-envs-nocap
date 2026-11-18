# Issue

**Title:** New programs anvi-setup-amrfinder and anvi-run-amrfinder to annotate genes with NCBI's AMRFinderPlus

## Description

This PR adds two programs that bring NCBI's [AMRFinderPlus](https://github.com/ncbi/amr/wiki) into anvi'o: `anvi-setup-amrfinder` downloads the AMRFinderPlus database, and `anvi-run-amrfinder` annotates the genes in a contigs-db with antimicrobial resistance genes, stress response genes (such as metal, biocide, heat, and acid resistance), and virulence genes. Among the various available tools to annotate microbial AMR genes, this is one of the most widely used, and its database is actively curated by NCBI, including AMR specific HMMs. AMRFinder is rather conservative and is based mostly on genes found in host associated microbes, but I tested it on a few Roseobacter genomes and the TREC metagenomic assemblies and its results align with what I expected, i.e. higher coverage of AMR genes in samples where we also found a high load of xenobiotics. I am mostly interested in using this within the TREC project. This is quite niche, but so is annotating cazymes and I think there is no harm in adding it to anvi'o. Like antiSMASH, AMRFinderPlus will not be part of the standard installation, so users need to install the program themselves, and `anvi-setup-amrfinder` then downloads its database. For me the advantage is that I can 'automatically' calculate PPCN on the metagenomic assemblies, which I think is ecologically more meaningful than looking at 'relative abundance' of genes.

AMRFinderPlus uses the amino acid sequences of anvi'o gene calls and maintains the gene caller id. It then stores the annotations and some additional information provided by AMRFinder as gene functions in the contigs-db, so that all downstream anvi'o programs can use them.

## New programs and artifact

- `anvi-setup-amrfinder` uses AMRFinderPlus's own `amrfinder_update` to download the newest database into `anvio/data/misc/AMRFinder/` (or a directory given with `--amrfinder-data-dir`). `--reset` only works on the default directory. It generates the artifact `amrfinder-data`.
- `anvi-run-amrfinder` exports the amino acid sequences of all genes in a contigs-db, runs `amrfinder --protein --plus --print_node`, and stores the hits in the contigs-db. `--amrfinder-data-dir` accepts both a directory managed by `amrfinder_update` and a single database version directory, so existing AMRFinderPlus databases (for instance on a cluster) can be used directly.

AMRFinderPlus is not a part of the standard anvi'o installation. It can be installed into an anvi'o environment with `conda install -c conda-forge -c bioconda ncbi-amrfinderplus`; a dry run showed no conflicts with the anvi'o development environment.

## What goes into the contigs database

Every hit is stored with six levels of information from the AMRFinderPlus database: the gene itself, three broader categories, and the `SCOPE`, which defines whether it is a well-established resistance gene (core) or a stress response, virulence, or AMR gene with less certain effects (plus). The `METHOD` records how the hit was found, for example HMM, BLASTP, or EXACTP. EXACTP is specific to AMRFinder and means that the amino acid sequence is 100% identical, over its full length, to a known reference protein in NCBI's database. Technically, each level is its own annotation source in the contigs-db (like `COG24_FUNCTION` and `COG24_CATEGORY` for COGs), so each one can be used with `--annotation-source` in downstream programs. It doesn't make sense to use `SCOPE` or `METHOD` in downstream programs such as `anvi-gen-function-matrix`, but I don't know how to solve this problem other than mentioning it on the program webpage or maybe as a warning when running the program? I haven't included either option yet. Here are the annotation sources provided by AMRFinder:

| Source | Accession | Function | Examples |
|:--|:--|:--|:--|
| `AMRFinder` | hierarchy node | gene name | `bla-B3`: subclass B3 metallo-beta-lactamase |
| `AMRFinder_CLASS` | class | class | BETA-LACTAM, MERCURY |
| `AMRFinder_SUBCLASS` | subclass | subclass | CARBAPENEM, ARSENITE |
| `AMRFinder_SUBTYPE` | subtype | subtype | AMR, METAL, BIOCIDE, VIRULENCE |
| `AMRFinder_SCOPE` | scope | scope | core, plus |
| `AMRFinder_METHOD` | method | method | HMM, BLASTP, EXACTP |

- The hierarchy node is used as the accession because gene symbols and names are not unique in the AMRFinderPlus database (for instance, `bla` is the symbol of both class A and subclass B3 beta-lactamases), while node identifiers are.
- AMRFinder uses an annotation hierarchy and always reports the most specific annotation.
- When AMRFinderPlus reports `NA` (for instance, there is no class for most virulence genes), there is no entry for that source.
- The database version is stored in the self table (`amrfinder_db_version`), and re-annotating a contigs-db requires `--just-do-it`.

## E-values

The AMRFinderPlus database contains curated cutoffs for each annotation, and AMRFinderPlus does not report e-values for HMMs. `anvi-run-amrfinder` recovers the e-values from the hmmsearch table that AMRFinderPlus keeps in its temporary directory when it runs with `--log` (anvi'o points `TMPDIR` to its own temporary directory to find it). Hits without an HMM match get an e-value of 0. If for example a future version of AMRFinderPlus stops keeping that table, the program stops with an explanation, and `--skip-e-values` lets users go on without e-values. One important difference to the e-values anvi'o generates with its other HMM based annotation sources is that AMRFinderPlus runs hmmsearch with `-Z 10000`, and does not care how many genes the contigs-db contains, so the e-values are not directly comparable. I did mention that on the program web page, which I hope is sufficient to avoid confusion.

## Optional full report

To generate an output table with all available information, users can use the flag `--full-amrfinder-report FILE`, which also includes the percent identity and coverage of the closest reference protein, the HMM e-value, the HMM bit score, and NCBI's curated HMM cutoff (from the database's `fam.tsv`).

## Deliberately left out

I decided to run AMRFinder on anvi'o gene calls rather than let the tool identify genes itself using BLASTX, which is an option in AMRFinder called 'nucleotide mode'. I am also leaving out the 'combined mode' that combines the HMM and BLASTP searches of the 'pre-identified' genes with the nucleotide mode. I tried this earlier and it did not generate any more hits in one of the TREC metagenomes, but it creates problems in the integration with anvi'o, as AMRFinder might identify new genes that are not in the contigs-db, for example genes that the gene caller missed or split because of a frameshift.
- I also left out the `--organism` option, which looks for known point mutations in housekeeping genes of pathogens.

## Testing

- I compared the `anvi-run-amrfinder` output to the previous results I generated by running AMRFinder on a Phaeobacter genome and I got the same results.
- Same for the TREC Riga surface metagenome (853,238 proteins) with database version 2026-05-15.1. For `anvi-run-amrfinder` to complete, it took 33 minutes with 8 threads on my computer.

## Other changes

- When this program becomes part of anvi'o dev, there will be three new entries in the shared argument dictionary in `anvio/__init__.py` (`--amrfinder-data-dir`, `--skip-e-values`, `--full-amrfinder-report`).
- The new artifact in `anvio/programsdata.py`, the two entry points in `pyproject.toml`, and the database directory in `.gitignore`.
- Docs for both programs and the new artifact, and AMRFinderPlus added to the list of annotation programs on the `functions` artifact page.

The code in this PR was written with the help of Claude.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `482973bc8f6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.