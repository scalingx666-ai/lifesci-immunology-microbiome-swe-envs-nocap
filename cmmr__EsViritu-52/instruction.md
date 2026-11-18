# Issue

**Title:** assembly_read_sharing_table: one streaming pass, O(assemblies²) memory

## Description

.

`assembly_read_sharing_table` stored every read name of every alignment in Python sets and then intersected the sets of all pairs of assemblies. With `-N 100` and many near-identical references, memory and run time grow with alignments × references. This PR computes the same table in one streaming pass:

- **Input:** it reads the read-grouped (unsorted) `*.filt.bam` that `minimap2_f` already writes before sorting, so all records of a read pair are adjacent. Both call sites (attempts 1 and 2) pass that file. A coordinate-sorted BAM is rejected with a clear error.
- **Counting:** for each read it collects the set of assemblies hit, and accumulates per-assembly totals and an assemblies × assemblies co-occurrence matrix (batched `numpy` updates). Memory is O(assemblies²).
- **Identity:** read identity is a running sum and count per contig instead of lists of floats.
- **Output:** same rows, same row order (assemblies by their first contig in the reference, pairs i ≤ j including self), same columns and dtypes. The average identities can differ in the last digits, because the summation order differs.

No new dependencies.

### Results (EsViritu 1.3.4, DB v3.2.4, paired NextSeq 2×151)

**Full sample from #51** (34.5 M pairs; 1.116 × 10⁹ alignments on 371 assemblies), `initial_read_comp_compare` table:

| | v1.3.4 | this PR |
|---|---|---|
| time in the function | 11,768 s | 3,630 s |
| peak RSS | 156 GiB (OOM-killed at 32 GB) | 0.33 GB |
| table | 49,480 rows | identical: all count/share columns and row order equal; identities max rel. diff 4e-12 |

**End to end** on 7 samples: original vs patched code, same container (`--keep True` so the intermediate tables can be compared).

- The samples:
  - 20k and 100k-pair test sets
  - two full Mpox-panel samples
  - one full 7.1 M-pair wastewater sample
  - 2 M-pair subsets of two SARS-CoV-2-rich wastewater samples
- All final outputs are identical: `detected_virus.info`, `assembly_summary`, `tax_profile`, coverage windows, consensus FASTA, readstats, fastp JSON apart from its command line.
- `initial_`/`second_read_comp_compare.tsv` are identical row by row.
- Time in this function on the 2 M-pair SARS-CoV-2-rich subset: 614 s → 223 s.

One thing the tests surfaced, unrelated to this change: in 1.3.4 the `*_read_comp_clust.tsv` and `detected_virus.assembly_summary.tsv` row order, and the element order inside `tax_profile` `assembly_list` (from `unique()`), differ between two identical runs. So those were compared as sets. Happy to send a small follow-up making them deterministic (`maintain_order=True` / sorting) if you'd like.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42aad529d911`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.