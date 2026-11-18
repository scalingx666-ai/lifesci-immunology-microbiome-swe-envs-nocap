# Issue

**Title:** fix: give rownames = "NCBI" bare identifiers

## Description

.

## Two defects propping each other up

`taxonomyRankEmpty()` was called without a `rank`, so it defaulted to `taxonomyRanks(x)[1]`, which here is `superkingdom` and is never empty. It flagged **zero rows**, so the filter never removed anything, and the block was duplicated verbatim.

Eleven rows are MetaPhlAn species groups and complexes that NCBI resolves no further than genus (`s__Pseudomonas_aeruginosa_group`, `s__Enterobacter_cloacae_complex`, and nine more). Because the rows then disagreed on their lowest rank, `getTaxonomyLabels()` prefixed **all 13,128** labels with their rank, which is what #316 reports:

| rows present | labels carrying a rank prefix |
|---|---|
| everything | 13,128 / 13,128 |
| drop just those 11 | 0 / 13,117 |

Naming the rank drops them and the prefixes go. That exposed the second defect: without a prefix the labels are bare *integers*, and duplicates reach `make.unique()`, which requires character and errors with `'names' must be a character vector`. The prefix had been hiding it.

## The duplicates are signal, not noise

NCBI has merged species that CHOCOPhlAn_201901 still reports separately, so 108 rows share 52 identifiers. This is the mirror image of #341, which is about splits.

| MetaPhlAn clades | one NCBI species |
|---|---|
| `Rhodobacter_sphaeroides` + `Rhodobacter_megalophilus` | 1063 *Cereibacter sphaeroides* |
| `Xanthomonas_hortorum` + `_gardneri` + `_cynarae` | 56454 *Xanthomonas hortorum* |
| `Borreliella_garinii` + `Borreliella_bavariensis` | 29519 *Borreliella garinii* |

Mostly bacteria (80 rows), not phages. They are partitioned reads of one organism, so they are **summed**, via `agglomerateByVariable()` so the `rowTree` stays consistent. Summing rather than averaging because these values are compositional: relative abundances sum to ~100 per sample, and with `counts = TRUE` they are literally read counts, so a mean would under-report every merged taxon by its group size.

## Both changes report themselves

The drop warns, lists what went, and points at the lossless option:

```
dropping 11 taxa from `HMP_2012.relative_abundance` with no species-level name:
  Streptococcus_dysgalactiae_group
  Lactobacillus_casei_group
  ...
These are MetaPhlAn species groups and complexes that NCBI does not resolve to a
species. Use rownames = "long" to keep every taxon.
```

The merge messages which clades went where:

```
merging 84 rows of `HMP_2012.relative_abundance` into 41 NCBI Taxonomy IDs,
summing their values:
  1063 <- Rhodobacter_sphaeroides, Rhodobacter_megalophilus
  29519 <- Borreliella_garinii, Borreliella_bavariensis
  ...
```

## The test was hiding this

`test-curatedMetagenomicData.R` stripped rank prefixes *and* uniquifying suffixes before asserting, so it passed while every user received tagged row names. It now asserts bare, unique, integer-coercible row names, which is what the test name claimed all along.

That test is also currently the **only** failure on `devel`: the strip had itself broken with `subscript out of bounds`, since an earlier line already coerced to integer.

## Verified

Simulated over the full shipped taxonomy restricted to tree tips: 10,363 rows in, 11 dropped, 43 merged, **10,309 out with zero prefixed and zero duplicated row names**. Column sums identical before and after the merge, confirming sum rather than mean. `rowTree` updated to 10,309 tips.

## Behaviour change worth noting

`rownames = "NCBI"` now returns fewer rows than `"short"` for the same query, because identifiers merge where names do not. `"long"` is unaffected and remains lossless. This follows from the identifiers themselves rather than from a choice here, but it is visible and is documented in #342.

## Left alone

`NAMESPACE` still carries two stale imports (`mia::taxonomyRanks`, `purrr::list_along`) that nothing uses. roxygen removes them on regeneration. Unrelated to this fix, so left for a separate change.

## Test plan

- [ ] `rownames = "NCBI"` returns bare integer row names with no `species:` prefix
- [ ] The drop warning fires and lists the 11 taxa
- [ ] The merge message lists the affected identifiers
- [ ] Column sums are unchanged by the merge
- [ ] The rewritten test passes without stripping anything
- [ ] `rownames = "short"` and `"long"` are unchanged apart from the 11 dropped rows

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd7a01346b53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.