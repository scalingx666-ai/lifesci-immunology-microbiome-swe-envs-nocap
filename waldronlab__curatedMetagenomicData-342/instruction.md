# Issue

**Title:** docs: explain how the three rownames vocabularies differ

## Description

.

## The report

Merging an external MetaPhlAn3 profile with curatedMetagenomicData by species name silently drops taxa that NCBI has reclassified since `mpa_v30_CHOCOPhlAn_201901` was built. MetaPhlAn3 reports `Bacteroides_dorei`, `rownames = "short"` gives `Phocaeicola_dorei`, and the rows never match. They appear as all-zero rather than raising an error, which is the worst way to find out.

## The data are correct, the documentation was not

`data-raw/rowData.R` resolves each clade's NCBI Taxonomy ID with `taxize::classification()`, so `"short"` and `"NCBI"` follow current NCBI taxonomy, while `"long"` keeps the MetaPhlAn clade string verbatim. Both behaviours are defensible. What was missing is that the documentation never said they were different vocabularies: it described `"short"` as just "(species name)", which is precisely the assumption that fails.

`rownames = "long"` is the default and already solves the reporter's problem, so this is a documentation fix rather than a code change.

## Scope

Wider than the reported example. **769 of 10,352 returned rows (about 7%)** sit under a different genus in the two schemes. The whole shipped taxonomy table has 1,394 of 13,117, but only 10,363 of its 13,128 rows are tips of `phylogeneticTree` and ever reach a returned object. Roughly half of the affected rows are phages, which MetaPhlAn names after the host (`s__Stx2_converting_phage_86` resolves to genus `Traversvirus`), so that half is a naming convention rather than a reclassification. The bacteria-only rate is 7.7%. Measured from the shipped `sysdata.rda` by comparing the species segment of each MetaPhlAn clade string against the resolved `species` column:

| MetaPhlAn3 | cMD `"short"` | species |
|---|---|---|
| Lactobacillus | Companilactobacillus, Lentilactobacillus, Limosilactobacillus, Ligilactobacillus, Levilactobacillus, Liquorilactobacillus, Secundilactobacillus, Lacticaseibacillus | ~98 |
| Mycoplasma | Mycoplasmopsis | 20 |
| Clostridium | `[Clostridium]` | 15 |
| Ochrobactrum | Brucella | 11 |
| Bacteroides | Phocaeicola | 8 |

The 2020 *Lactobacillus* split is the big one, not Bacteroides.

## Changes

- `@section Taxonomic names` on `curatedMetagenomicData()`: which option matches MetaPhlAn and under what condition, why `"short"` and `"NCBI"` drift from it, that the failure is a silent non-match, and that ID joins should use the integer `rowData()` column rather than the `rownames = "NCBI"` labels, which carry a rank prefix (#316).
- `@param rownames` in both functions flags that the three options are different vocabularies. `returnSamples()` links to the section on the `curatedMetagenomicData()` help page, since the section lives there.
- The same point, shorter, in the vignette.

## A note on man/

Edited by hand rather than regenerated, but not for the reason I first gave. Regenerating does **not** churn every man page: with roxygen2 8.0.0 it rewrites exactly one `.Rd`, swaps `RoxygenNote: 7.3.2` for `Config/roxygen2/version: 8.0.0` in `DESCRIPTION`, and drops two stale `importFrom` lines from `NAMESPACE` (`mia::taxonomyRanks` and `purrr::list_along`, neither used nor tagged anywhere in `R/`). Those last two are a real cleanup, but they belong in their own change rather than riding along with a documentation fix.

Both `.Rd` files are now **byte-identical to roxygen2 8.0.0 output**, verified by regenerating into a scratch copy and diffing, so a future `roxygenise()` is a no-op for them.

## Not addressed here

- `rownames = "NCBI"` emits `species:`/`genus:` prefixes instead of bare IDs (#316), so the stable-key workaround needs that fixed to be pleasant to use.
- An exported crosswalk helper would be better than asking users to assemble one. Worth designing alongside MetaPhlAn4 (#294) and GTDB (#301) rather than retrofitting onto v3.

## Test plan

- [ ] `tools::parse_Rd()` passes on both man pages (verified locally)
- [ ] `R CMD check` raises no Rd warnings
- [ ] Rendered help for `curatedMetagenomicData` shows the Taxonomic names section
- [ ] Vignette builds

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---

**Update after Copilot review.** Five findings, all valid and all traceable to one wrong assumption of mine: that `rowData()` exposes names and NCBI IDs together. It does not. The function assigns `rowDataLong` for `"long"` and `"short"` and `rowDataNCBI` for `"NCBI"`, so one object carries a single vocabulary. The three-way crosswalk claim is removed, ID joins now point at the integer `rowData()` column, `returnSamples()` links to the right help page, exact MetaPhlAn matching is qualified by database version, and "all-zero rows" is corrected to a failed match, which is the only guaranteed behaviour. Fixed in 53f95a3.

---

**Second update.** Copilot's later round flagged that `rowDataLong`/`rowDataNCBI` are generated offline into `sysdata.rda`, so describing them as "current NCBI taxonomy" promises a live lookup the package never does. Corrected to a snapshot taken when the packaged taxonomy is built. A review pass also caught that the 10.6% figure counts rows that are never returned, that about half the affected rows are phages rather than reclassifications, that a `"long"` object does expose a clade-to-name crosswalk on its own, and that genus identifiers are not stable across reclassification even though species identifiers are. All verified against `sysdata.rda` before changing. Fixed in 4d72be6.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23c8bc3e584a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.