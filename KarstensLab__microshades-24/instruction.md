# Issue

**Title:** Add option to change legend orientation

## Description

Hello!

As introduced in issue #17, the `custom_legend` function currently does not provide an option to change the orientation of the custom legend.

This pull request proposes a new parameter to `custom_legend`, `legend_orientation`, that allows for specification of the legend orientation to be horizontal or vertical. The default is vertical, which is how legends are produced currently.

This will allow users to call the `plot_grid` function from the `cowplot` package to produce plots with a custom legend below the plot.

Below are images showing example plots, with a PDF showing how to reproduce these plots: [legend_orientation_doc.pdf](https://github.com/KarstensLab/microshades/files/12403245/legend_orientation_doc.pdf).

### microshades plot of phyloseq Global Patterns data with vertical legend to the side (default):
<img src="https://github.com/KarstensLab/microshades/assets/90294056/2996fe8a-c7d3-405d-99ed-5fe67ebb3631" alt="microshades plot with vertical legend to the side" width="450">

### microshades plot of phyloseq Global Patterns data with horizontal legend below:
<img src="https://github.com/KarstensLab/microshades/assets/90294056/a774a5e4-8ae1-4469-969c-c4a9894799be" alt = "microshades plot with horizontal legend below" width="400">
<br/>
<br/>

Thank you!

Best,
Anagha

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da0b352df9f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.