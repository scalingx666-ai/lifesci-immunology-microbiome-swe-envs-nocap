# Issue

**Title:** Merge the Exercises chapter into other chapters

## Description

.

The Exercises chapter (chapter 26) only contained general tips and two links to R/Bioconductor basics. The exercises themselves are at the end of each chapter. This PR removes the chapter and moves its content to where it fits:

- **Chapter 1, Bioconductor section (`intro.qmd`):** the two Carpentries lessons on R and Bioconductor basics, as suggested in the issue.
- **Training chapter (`training.qmd`):** a new "Exercises" section with the tips for exercises and a link to the example solutions (Appendix C). These tips apply to the exercises in all chapters, and the Training chapter already pointed readers to the Exercises chapter for self-study. Both of those references now link to the new section.
- **`_book.yml`:** `pages/exercises.qmd` removed from the book.
- **Parts merged:** with the Exercises chapter gone, the "Training" part only had one chapter. It's now combined with "Support & resources" into one part, "Training & resources" (Training, Support, Resources, Contributions).

No other chapter referenced the removed chapter.

## Testing
Rendered `intro.qmd` and `training.qmd`. All cross-references resolve, including the link to the example solutions (Appendix C). The full book was not rendered.

## Note
Removing a chapter renumbers the chapters after it in the Training part and later (e.g. Support, Resources, Contributions).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5de03668ca4d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.