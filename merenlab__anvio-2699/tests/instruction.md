# Issue

**Title:** Collapse parallel reaction elements in the KGML pathway network walker

## Description

KEGG pathway network walking (anvio/kgmlnetworkops.py) enumerates chains of compounds linked by reactions, analyzing KGML files underlying the KEGG maps. Alternative KOs that encode the same reaction can be found as separate KGML reaction elements. There is a combinatorial explosion in the number of walks across reaction elements in pathways with many parallel KGML reaction elements, making walks of complex pathways intractable. For example, a single Fatty Acid Biosynthesis (00061) backbone route can generate millions of chains through alternative KOs.

To solve this problem, parallel reaction elements equivalent for walking (same KEGG reaction name, same compound endpoints, same type, same gap status) are folded into a single `CollapsedReaction`, and chains are walked over these collapsed edges. Constituents are retained so chains can be expanded back to element level at any time. `KGMLNetworkWalker.get_chains()` returns collapsed chains by default. `KGMLNetworkWalker.get_chains(expand=True)` and `expand_chain()` reconstruct element-level chains. `metabolicexchanges` is unaffected -- it consumes chains by KEGG reaction/compound name (collapse-invariant), so it gains the speed-up for free.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9cc7db2337cd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.