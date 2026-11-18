# Issue

**Title:** Proposed vaccine author list

## Description

<!-- Hi there! Please use the template below as a guide for opening a pull request.
This template is designed to help the pull request process go smoother.
If anything doesn't make sense to you, please open the pull request anyway and leave entries blank as needed.
Thank you for your contribution!! -->

### Description of the proposed additions or changes
<!-- If the additions or changes aren't self explanatory feel free to leave a description or notes here. -->
Here is my proposed plan for author order. Please feel free to indicate if you think something doesn't look right. Here's the data I pulled:

Author/username | contributions | Order - Trad | Order - Novel | # lines
-- | -- | -- | -- | --
Anthony Gitter   | software and editing | 8 | 8 | 39
Casey Greene | mRNA | 7 | 9 |  
HM Rando   |   | 1 | 1 | 5514
Ronan Lordan  |   | 2 | 2 | 1055
likhithakolla   | mRNA | 5 | 3 | 116
Elizabeth (Ellie) Sell  | DNA | 4 | 4 | 42
Alexandra Lee  | whole-virus | 3 | 5 | 375
nilswellhausen    | novavax | 3 | 5 | 205
NAIKA86   | COVAXIN | 3 | 6 | 36
John J. Dziak   |   | ack | ack | 2
Consortium |   | 6 | 7 |  

I made a note where people had taken a major role in contributing to a particular vaccine write-up.

### Related issues
<!-- GitHub will link issues to pull requests if you list the related issue numbers like "#2, #17". -->
#830

### Suggested reviewers (optional)
<!-- If there are particular people you think should review this pull request, please list their GitHub handle like "@rando2".-->


### Checklist
<!-- Please mark the following tasks as complete by putting an "x" in the box like "[x]".
If a particular item is not applicable to your pull request, please delete the item. -->
- [ ] Text is formatted so that each sentence is on its own line.
<!-- see why this is recommended here:https://github.com/greenelab/covid19-review/blob/627a5f45a2d1fcb2150d1466df63bb848f22a3d4/USAGE.md#manubot-markdown -->
- [ ] Pre-prints cited in this pull request have a GitHub issue opened so that they can be reviewed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a98d795aa8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.