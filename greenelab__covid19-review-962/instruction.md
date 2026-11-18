# Issue

**Title:** Updates to figures for Therapeutics manuscript

## Description

<!-- Hi there! Please use the template below as a guide for opening a pull request.
This template is designed to help the pull request process go smoother.
If anything doesn't make sense to you, please open the pull request anyway and leave entries blank as needed.
Thank you for your contribution!! -->

### Description of the proposed additions or changes
<!-- If the additions or changes aren't self explanatory feel free to leave a description or notes here. -->
I was wondering if I could ask for some initial feedback on this adjustment to the CSSE figure for the intro in Therapeutics
We had gotten feedback from internal reviews that it didn't really communicate that much information, and since I reframed the intro of the therapeutics standalone to be about the differences between COVID-19 and SARS/MERS, I was hoping this might help illustrate it.
Obviously we have a huge issue of scale...
I can definitely clean this up but wanted to make sure the concept worked before I jump into aesthetics!

![csse-deaths](https://user-images.githubusercontent.com/8975841/118691049-b0154380-b7d6-11eb-8f32-5c305fd3c137.png)

UPDATE 7/29: I am also adding in minor adjustments to the clinical trials figure based on previous feedback

### Related issues
<!-- GitHub will link issues to pull requests if you list the related issue numbers like "#2, #17". -->
provides some steps towards #736 

### Suggested reviewers (optional)
<!-- If there are particular people you think should review this pull request, please list their GitHub handle like "@rando2".-->
@ajlee21 @agitter @cgreene @cbrueffer @nilswellhausen @RLordan 

### Checklist
<!-- Please mark the following tasks as complete by putting an "x" in the box like "[x]".
If a particular item is not applicable to your pull request, please delete the item. -->
- [ ] Text is formatted so that each sentence is on its own line.
<!-- see why this is recommended here:https://github.com/greenelab/covid19-review/blob/627a5f45a2d1fcb2150d1466df63bb848f22a3d4/USAGE.md#manubot-markdown -->
- [ ] Pre-prints cited in this pull request have a GitHub issue opened so that they can be reviewed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ee51e5e40c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.