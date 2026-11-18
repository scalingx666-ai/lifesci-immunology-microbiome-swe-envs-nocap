# Issue

**Title:** Visualize vaccine distrubtion by technology

## Description

<!-- Hi there! Please use the template below as a guide for opening a pull request.
This template is designed to help the pull request process go smoother.
If anything doesn't make sense to you, please open the pull request anyway and leave entries blank as needed.
Thank you for your contribution!! -->

### Description of the proposed additions or changes
<!-- If the additions or changes aren't self explanatory feel free to leave a description or notes here. -->
@RLordan I think we had discussed this ages ago, but here are some figures to show the distribution of each vaccine type. I was thinking to add them to the manuscript where we end up talking what has been approved. The colors correspond to how many different vaccines of each type have been rolled out in each country (according to OWID)

![RNA](https://user-images.githubusercontent.com/8975841/145895561-9d4c20b2-b239-4e0c-b8f3-b50b381ebc58.png)
![inactivated_whole-virus](https://user-images.githubusercontent.com/8975841/145895546-c5773f9d-af51-4c7c-ad85-dcdf8a092fe6.png)
![non-replicating_viral_vector](https://user-images.githubusercontent.com/8975841/145895549-bb83566e-d148-4320-95c8-cf62a7c2e66d.png)
![protein_subunit](https://user-images.githubusercontent.com/8975841/145895558-bff056e8-508b-46c3-97db-d79bc1d105a0.png)

This PR (especially the code) needs to be cleaned up, but I wanted to get your thoughts on the figures first. Originally I was trying to make a four-panel graph, but that is hard to make forwards-compatible (by which I mean, if more types of vaccines are approved, we would need more panels).

I'll tag someone for technical feedback after Ronan approves the actual objective of the PR, which was to visualize some stats he collected!

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f06485a1768`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.