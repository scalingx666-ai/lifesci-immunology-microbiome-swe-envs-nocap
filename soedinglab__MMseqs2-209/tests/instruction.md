# Issue

**Title:** Make prettier help pages

## Description

This PR implements help pages in MMSeqs2 that are (I think) easier to parse and more like help pages of other linux commands and bioinformatics tools.

Changes:
  - Put the default value in square brackets at the end of the description, instead of the second column.
 - Add the argument type to options, e.g. `-e FLOAT`
 - Specify the possible range of options by `(range FROM-TO)` at the end of the description, before the default value
 - Add some extra spacing (maybe not necessary)
 - Don't write `XXX options` for each option set, instead write the option set name alone
 - Add required positional argument descriptions when specifying `-h`. Currently I don't think any commands actually have this description, so maybe this shouldn't be shown.

Old:
![image](https://user-images.githubusercontent.com/516060/58734649-fc86cf00-83c5-11e9-95af-dd4fce904907.png)

New:
![image](https://user-images.githubusercontent.com/516060/58734656-07416400-83c6-11e9-967b-9927418f818a.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf150146df85`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.