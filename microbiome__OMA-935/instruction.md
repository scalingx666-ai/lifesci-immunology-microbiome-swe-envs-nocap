# Issue

**Title:** Use tidySummarizedExperiment filter() for the zero-variance filter

## Description

Proposed change to #882: write the zero-variance filter with tidyomics syntax.

```r
library(tidySummarizedExperiment)

tse_sub <- tse |> filter(sd > 0)
```

instead of

```r
selected <- rowData(tse)[["sd"]] > 0
tse_sub <- tse[selected, ]
```

## Details
- **Same result:** checked on the chapter's data (GlobalPatterns). The same 18988 features and counts are kept, and the result is still a `TreeSE` with its tree.
- **Text:** a short paragraph introduces `filter()` from tidySummarizedExperiment and links to the Data wrangling chapter.
- **`DESCRIPTION`:** `tidySummarizedExperiment` is added, since the chunk runs during the book build.

## Notes
- **Why not tidySingleCellExperiment:** the book already uses it, but it can't do this. Its tibble view has one row per sample, so `filter(sd > 0)` fails; it can only filter samples (e.g. `filter(SampleType == "Feces")`).
- **Printing:** with tidySummarizedExperiment loaded, an explicit `print(tse)` shows the tibble view, but typing the object's name prints it as usual. In the rendered book the objects print as before.
- **Extra metadata:** `filter()` adds a `latest_filter_scope_report` entry to `metadata()`. It's harmless.

The chapter renders.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `590502b69fc2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.