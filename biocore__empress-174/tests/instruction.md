# Issue

**Title:** Add Empress class and add support for OrdinationResults in q2-empress

## Description

This PR moves over the code from _plot.py into a new class `Empress`. In addition this allows support for visualizing ordinations and phylogenies simultaneously. Here's an animated gif of this working with brush selection (related to ).

![empress-pr](https://user-images.githubusercontent.com/375307/84715877-a3cd9a00-af26-11ea-8e6d-0bcd74f34fa2.gif)

The example above shows how selecting a group of samples of different colors shows the unique branches per color (similar to UniFrac comparing groups). When a single sample or group is selected, all the features for that group are highlighted in Empress.

`qiime empress plot` now accepts an optional ordination object.
The majority of the code for the Empress class was inspired by the Emperor object.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e4bbd3cc53a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.