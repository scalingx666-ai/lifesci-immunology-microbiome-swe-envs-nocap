# Issue

**Title:** Improvements to label sizes

## Description

This PR adds a stable scaling for labels in the plot. It removes the changes put in as part of #667. While this was not a problem for axes labels, it was a big issue for biplot labels, see for example this plot and notice how the text has varying sizes:

![screen shot 2018-07-20 at 9 40 32 am](https://user-images.githubusercontent.com/375307/43014487-20829c58-8c01-11e8-82e9-70129401dfbb.png)

And after this PR, all the text in the scene has the same size, making it for a better looking plot:

![screen shot 2018-07-20 at 9 43 06 am](https://user-images.githubusercontent.com/375307/43014543-57688714-8c01-11e8-95cf-57e929b10985.png)

These changes make the text size constant by determining a scene-wide scaling (no more strange scalings scattered all over the place woooohooo! 🎉 ).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd53d099ae09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.