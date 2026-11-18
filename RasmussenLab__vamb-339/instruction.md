# Issue

**Title:** Make TaxVamb taxonomy output format well-defined

## Description

Previously, the taxonomy format input to TaxVamb was poorly defined, and did not correspond to the format output by Taxometer.
This had a couple of bad consequences:
1. It made it more difficult to specify what format the user should format the supplied taxonomy with
2. The taxonomy format was too tightly coupled to the particular program that generated it (an artifact from when we just used mmseqs2, I believe)
3. It required three extra command-line params just to specify columns and separator for the taxonomy
4. It required the use of general-purpose parsers in Pandas, which is fragile.

Now, with these changes, we have:
* Three command-line arguments removed
* __main__.py no longer depends on Pandas, it is also thoroughly statically analyzable
* More robust parsing with better error messages.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34b91bd97e33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.