# Issue

**Title:** Add option to not use relative abundance in prep_mdf

## Description

Hi microshades team,

Thanks for this awesome tool! I've been using it a lot lately for microbiome analysis, and I've started also using it with other -omics that aren't compositional. Because these other -omics (e.g. metabolomics, lipidomics) aren't compositional, I don't always want the data to be converted to relative abundances, so I created my own version of `prep_mdf()` to do so. However, I felt that this would be a good addition to the microshades, so here's this pull request :)

I added an argument to `prep_mdf()` that is `as_relative_abundance`, and it defaults to `TRUE`, so all existing code should work with no changes. The function now checks if `as_relative_abundance==TRUE`, and if so, it does the same thing it did before. If not, it simply skips the relative abundance conversion.

After making this change, all tests still passed when I ran them.

Please let me know your thoughts on this potential change, as I'd love to have an option to not use relative abundances built into microshades.

Thanks,
John

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af1573ade3c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.