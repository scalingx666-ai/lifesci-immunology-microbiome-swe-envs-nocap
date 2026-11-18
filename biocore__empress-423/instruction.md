# Issue

**Title:** NEW Add reverse argument for Colorer

## Description

#418 

This PR adds functionality to Colorer to support reversing color maps. I have also integrated the reverse with the feature metadata coloring UI element.

You can see the feature in action [here](https://drive.google.com/file/d/1rGFY7TVp4eM9XoPmtvsXszomlkbFZfto/view?usp=sharing).

Notes/questions:

Custom color maps are not supported (my understanding is that the user supplies an object that performs the mapping, which is unordered, so cannot be “reversed”)

Are there other places where you would like me to implement the UI elements for reversing the color map?

Tests:

[x] Colorer with reverse=true works with discrete color map

[x] Colorer with reverse=true works with continuous color map

[x] Colorer with reverse=true works with ordinal color map

[x] Emperor.colorByFeatureMetadata switches the color values when reverse=true

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a76ebf27a8c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.