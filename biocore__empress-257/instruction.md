# Issue

**Title:** DEV: Add make-dev-page.py

## Description

This creates a development page of Empress (optionally a tandem plot)
using the moving pictures tutorial data. To see changes from the
JavaScript and CSS files you can reload the generated page from the web
browser.

In the animated GIF below, I show how to see changes to the source by reloading the page (initially the log message is not visible in the console):

![dev-cycle](https://user-images.githubusercontent.com/375307/87369666-e9857e80-c535-11ea-8140-cc4900c907db.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2fc199b870d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.