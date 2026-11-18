# Issue

**Title:** += anvi-run-antismash, anvi-script-gen-antismash-matrix

## Description

This was a PR originally proposed by @jessika-fuessel at #2745. While going through that PR I started making changes, and somehow I screwed it up and now instead of commits linked to the original PR, we have a new PR with changes by @jessika-fuessel and me.

My changes are largely anvi'o-specific changes and include fixing some odd behavior by Claude, more rigorous checks with output file dir, better tracking contig names, update to error messages, excluding noncoding genes from downstream analyses, and so on.

The original message by @jessika-fuessel is below.

---

I wanted to include an option in anvi'o to annotate BCG with **antiSMASH** and store the annotations along with other functional annotations in the contig-db. The program anvi-run-antismash generates annotations of the individual genes in BGCs using HMMER and smCOG, antiSMASH's own database for of secondary-metabolism Clusters of Orthologous Groups, and it annotates BGC by 'region', which include several genes but a common 'biosynthetic goal'. antiSMASH needs to be run in its own conda environments as several of it's dependencies overlapp with those of anvi'o, but it requires different versions. However, once it is installed and you run it from your anvi'o environment, anvi'o will find it (or if not, there is an optional flag pointing to the location of antiSMASH).

Running the program creates four individual annotations that annotate the same genes, but at different levels:
- `antiSMASH` (smCOG individual gene functional annotation)
- `antiSMASH_ROLE` (biosynthetic / regulatory / transport / ...)
- `antiSMASH_DOMAIN` (each biosynthetic domain the gene carries)
- `antiSMASH_REGION` (which BGC region the gene belongs to)

If user would like to run it on several contig-dbs, it can accept an external-genome file and will annotate all contig-dbs listed.

**anvi-run-antismash** creates a new directory for each contig-db within it sores two dataframes, the 'antismash_genes.txt and the antismash_regions.txt. It also creates a browsable html output and stores a set of files needed to generate that interactive output.

The script **anvi-script-gen-antismash-matrix** relies on the stored antiSMASH annotations and creates a matrix across genomes either for --regions or --genes based on the external-genomes.txt. It also creates a 'per gene-bride' document linking each matrix cell to individual genes.

While my main motivation to integrate antiSMASH into anvi'o came from my need to annotate biosynthetic gene clusters in the TREC metagenomes, there is also a feature request from May 2026 #2619 suggesting the same. I wanted to ping Guillermo Rangel-Pineros, who created the feature request, in case they have some more suggestions for additional features, improving the code, testing the tool....

I created the code with the help of Claude AI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4251778156a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.