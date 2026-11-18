# Issue

**Title:** Add optional abbreviated parameters for the standalone CLI; add some more context to the README

## Description

This makes the CLI a bit easier to use if you're in a hurry, since potentially generating a visualization can be as short as:

```bash
$ empress tree-plot -t tree.nwk -o viz
```

I also updated the README a bit to document this, and to make it a bit fancier in general. (One of the changes is consistently using hyphens in filenames for some of the early examples. I didn't modify the QIIME 2 tutorial since the filenames there [IIRC] were designed to be consistent with Q2's tutorial files, some of which have underscores instead of hyphens.)

Not all of the parameters in the standalone CLI have short equivalents (e.g. `--filter-extra-samples` will still have to be written out in full). I think this is reasonable, since arguably part of the rationale for many of these parameters is requiring the user to acknowledge e.g. "yes I recognize that I am asking the program to filter out certain samples right now".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `241b6e873d3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.