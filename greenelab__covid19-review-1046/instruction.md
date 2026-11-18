# Issue

**Title:** Reorganize clinical trials fig to meet journal requirements

## Description

<!-- Hi there! Please use the template below as a guide for opening a pull request.
This template is designed to help the pull request process go smoother.
If anything doesn't make sense to you, please open the pull request anyway and leave entries blank as needed.
Thank you for your contribution!! -->

### Description of the proposed additions or changes
<!-- If the additions or changes aren't self explanatory feel free to leave a description or notes here. -->
I had to split the figure up into each panel for the original submission (due to file size requirement of < 20 Mb). The feedback from the journal was: 

> Figure 2 was submitted in multiple panels. Figures must be assembled to form complete figures prior to submission (Figure 1 is okay due to sizing and fonts size.)

> Please review the guidelines for acceptable figure files below and resubmit the figures at your earliest convenience. Figures should be provided at 100% of their print dimensions so that no reduction or enlargement is necessary. Figures should be no more than 6.87 inches wide (approximately 17.46 cm or 41.25 picas wide) and 9.06 inches high (approximately 23.01 cm or 54.37 picas high), while meeting all other criteria listed below for the specific file type being submitted. We also ask that you remove any figure legend text (although note that figure keys should be included), figure identifiers ("Figure 1") and/or excess white space from around the figure prior to increasing your image resolution and resizing your figures. Final font/text size must not fall below 6 points.

I reorganized the figure in the hopes that this will improve readability given these constraints. Here's what it looks like now:

![ebmdatalab-trials](https://user-images.githubusercontent.com/8975841/134712216-29ad5b8f-e6a2-480e-aea4-44d383cf082b.png)

I'll wait for feedback on this PR to resubmit!

### Related issues
<!-- GitHub will link issues to pull requests if you list the related issue numbers like "#2, #17". -->


### Suggested reviewers (optional)
<!-- If there are particular people you think should review this pull request, please list their GitHub handle like "@rando2".-->


### Checklist
<!-- Please mark the following tasks as complete by putting an "x" in the box like "[x]".
If a particular item is not applicable to your pull request, please delete the item. -->
- [ ] Text is formatted so that each sentence is on its own line.
<!-- see why this is recommended here:https://github.com/greenelab/covid19-review/blob/627a5f45a2d1fcb2150d1466df63bb848f22a3d4/USAGE.md#manubot-markdown -->
- [ ] Pre-prints cited in this pull request have a GitHub issue opened so that they can be reviewed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `937aa4d60452`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.