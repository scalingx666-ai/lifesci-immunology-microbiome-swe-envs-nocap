# Issue

**Title:** Fix seed/gene matching, bin modes, BLAST search, and error handling in `anvi-integrate-trnaseq`

## Description

This branch fixes problems in `anvi-integrate-trnaseq`, with some shared fixes in `anvi-compute-trnaseq-functional-affinity`. Several fixes affect how seeds are matched to tRNA genes.

## Seed/gene matching
- Genes in different contigs databases that share gene caller IDs no longer compete for one seed. Before, integrating several genomes silently dropped seeds, because seeds were being keyed by GCID but not source database.
- Only one seed is chosen per gene by fewest mismatches then highest coverage. Before, hits were stored per seed, so a seed chosen for one gene also retained equally good hits to genes that other seeds were chosen for. A gene could therefore be stored with seeds that matched better and worse, and a seed could appear to come from two genomes, affecting both `--unambiguous-genome-assignment` and the seed assignment in the calculation of affinity.
- For A34 genes, I34 (read as G) counts as a match. The mature I34 seed still replaces a rarer exact A34 seed when at least 10x as abundant. Before, the A34 branch of the code could raise an IndexError, and it left a gene without any seed whenever its 10x test failed, such as with partial inosination or when two G34 seeds competed.
- Unmodified nucleotides are read from the aligned gene position. Before, they were offset for seeds lacking the gene's 5' end, and the G-1 of tRNA-His read the gene's last base.
- Tied seed permutations now resolve as documented. Before, "most genes hit" counted gene-bin rows. "Fewest permuted positions" scored an unpermuted seed and a one-position permutation alike. "Favor the 5' end" followed a table order scrambled by a merge. A seed could then go to the wrong genome's gene and record a variant as the unmodified nucleotide.
- `--unambiguous-genome-assignment` judges each seed by the genes chosen for it, dropping a seed only if those genes span genomes, or a bin and unbinned contigs. Before, the flag ran before the per-gene choice and judged each seed by all its equally good hits. A seed tied with another genome's gene was dropped even when a better seed was chosen for that gene. Dropping a gene's best seed early also let a worse seed take the gene, such as a seed 100x rarer than the one dropped.

## BLAST search
- Seeds are searched with blastn, using a word size set by the shortest seed and `--max-mismatches`, rather than the megablast default word size of 28, a length which is less likely to occur within a tRNA transcript without modification mismatches. After BLAST, each hit is extended to the whole seed and its mismatches recounted. Before, megablast missed alignments with a positive value of `--max-mismatches` — for 3 substitutions, 38% of full-length seeds and 92% of 3' fragments — and mismatches very close to either end of a seed never matched, as they stopped the alignment.
- Every hit is reported instead of the default of BLAST's first 500 per seed.

## Bins, collections and internal genomes
- `--collection-name`, `--bin-id`, `--bin-ids-file`, and internal genomes crashed and now work. The same Collections calls are fixed in `anvi-compute-trnaseq-functional-affinity`.
- Seeds are matched against all genes of the contigs database, so a seed that better matches a gene outside the bins is not assigned to a gene in the bins, but only hits to genes in the requested bins are stored. Before, hits to genes outside the bins were stored with empty bin columns, as if their contigs were unbinned. With `--bin-id bin_A`, for example, genes in bin_B of the same collection were stored in the tRNA-seq contigs database as unbinned, the affinity calculation ignored them, and subsequently integrating bin_B in another integration run stored bin_A's genes a second time as unbinned.
- A binned hit is stored once, not once per split of its contig — any contig over the 20 kb split length had duplicate rows. Each contigs database's genes are also written to BLAST once, not once per bin, which had multiplied BLAST's work and could exhaust its then limit of 500 hits per seed.
- `--list-genomes` works for databases with bins.

## Reruns and temporary files
- Integrating a genome again replaces its stored hits instead of duplicating them, and `entry_id` continues when appending.
- Without `-u`/`-d`, temporary files go to new directories for each run, removed after program completion. `--blast-dir` is created if missing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `652f09d2fdc2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.