# Issue

**Title:** Support exporting all barplot legends, including color gradient and length legends; export collapsed clade shapes and barplots

## Description

Part of the work on #303.

.

Required some substantial refactoring to the way gradient SVGs are stored in Empress, in order to make it easier to scale these differently within a legend.

Also as part of this PR, slightly changed the way numbers are formatted in the Tree Statistics (so now commas are used as thousands separators [at least for English locales], etc.)

TODOs:

- [x] Add more vertical padding at the end of gradient and length legends (currently the text is flush with the surrounding border, which looks a bit too close for comfort)
- [x] Show a warning (for both gradient ~~and length legends [#391]~~) if there are missing / non-numeric values in the field. Currently this warning (which is already shown for gradient legends in the interface) is not included.
- [x] Refactor legend exporting code so that there isn't a notion of "rows" any more, so each legend can arbitrarily increase its vertical space without messing up other legends (all that should be kept track of are the height and width of each legend).
- [x] Unbreak tests (the colorer and legend tests, and maybe more, are extremely broken by these changes)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd159e17e151`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.