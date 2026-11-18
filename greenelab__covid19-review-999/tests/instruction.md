# Issue

**Title:** Add x-tick labels to CSSE figure

## Description

<!-- Hi there! Please use the template below as a guide for opening a pull request.
This template is designed to help the pull request process go smoother.
If anything doesn't make sense to you, please open the pull request anyway and leave entries blank as needed.
Thank you for your contribution!! -->

### Description of the proposed additions or changes
<!-- If the additions or changes aren't self explanatory feel free to leave a description or notes here. -->
Per the suggestion in #996, this add in x-axis labels for the CSSE figure.
I also adjusted the matplotlib code to make it easier to apply changes to all panels

Here is the new figure:
![csse-deaths](https://user-images.githubusercontent.com/8975841/129268166-cb55473c-0668-4232-86ae-63f1d1d84521.png)


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2ee4e4c1d62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.