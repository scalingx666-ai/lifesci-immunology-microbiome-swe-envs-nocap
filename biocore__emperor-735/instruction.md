# Issue

**Title:** Add a search bar to the controllers

## Description

This PR adds a search bar to filter down values in any given category. This is useful for large datasets. Here's an animated gif showcasing how the search bar works in the color, visibility and scale controllers:

![search-bar](https://user-images.githubusercontent.com/375307/64880309-bec45400-d60c-11e9-93ed-6d9031c76370.gif)

The bulk of the changes are in view-controller.js and a lot of other minor changes happened due to updated code style guidelines.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d4dde02bf9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.