# Issue

**Title:** Add figures to methods and edit text

## Description

Add figures from #944 and #1034

There are several changes to automated statistics, new figures, and a manual reference that will need to be checked carefully in the artifacts before merging.  I started some text edits, most notably shortening the abstract, but did not yet do my final proofreading.

I'm proposing we remove the references to individual manuscripts that haven't hit the preprint stage yet if we need to save space:
> These manuscripts cover a wide range of topics including the fundamental biology of SARS-CoV-2 (pathogenesis [@individual-pathogenesis] and evolution [@individual-evolution]), biomedical advances in responding to the virus and COVID-19 (pharmaceutical therapeutics [@individual-pharmaceuticals], nutraceutical therapeutics [@individual-nutraceuticals], vaccines [@individual-vaccines], and diagnostic technologies [@individual-diagnostics]), and biological and social factors influencing disease transmission and outcomes [@individual-inequality].

They took up a few lines of references in the prior DISCO submission and aren't that informative:
![image](https://user-images.githubusercontent.com/3532898/133196447-b6cdbcf7-b982-4809-baa8-5eefc5237797.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5611bd91a215`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.