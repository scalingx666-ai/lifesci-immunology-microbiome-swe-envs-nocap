# Issue

**Title:** Minor revisions to novel vaccines

## Description

<!-- Hi there! Please use the template below as a guide for opening a pull request.
This template is designed to help the pull request process go smoother.
If anything doesn't make sense to you, please open the pull request anyway and leave entries blank as needed.
Thank you for your contribution!! -->

### Description of the proposed additions or changes
<!-- If the additions or changes aren't self explanatory feel free to leave a description or notes here. -->
We thank the reviewer for their kind words and helpful suggestions. We have made the following changes to the manuscript:

3) Line 239 - This reference is not available

This work in progress is currently hosted on the GitHub pages rendering of the broader COVID-19 Review Consortium project. However, we suspect many readers may encounter a lag when accessing the bookmarked link due to the large amount of material on this page. We are working on identifying a solution to this problem, but in the meantime, we will update the reference to refer to the COVID-19 Review Consortium project itself, which includes this manuscript.

4) Line 276 - Malaria is not a bacterial disease

Thank you for catching this error. This line has been corrected to identify malaria as a parasitic disease.

**5) Line 683 - 2,686 represents 68% of the participants in the trial **
Thank you for catching this unclear sentence. It has been rephrased to state: Among these participants, 3,179 (80%) had received at least one dose of an mRNA vaccine, and of those, 2,686(84%) were fully vaccinated, corresponding to 68% of trial participants overall.

6) Line 266 and 287 - Which immune stimulant molecules? Which two vaccines?

Line 266 has been revised to state: "Plasmids can also be designed to act as adjuvants by encoding molecules such as cytokines that supplement the immune response [@doi:10.1358/dot.2018.54.5.2807864]."
Line 287 erroneously identified the number of veterinary plasmid-vectored DNA vaccines. This line has been modified to read: Prior to COVID-19, however, plasmid-vectored DNA vaccines had been approved for commercial use only in veterinary populations [@doi:10.1016/B978-0-323-35761-6.00067-5; @doi:10.5772/intechopen.76754; @doi:10.1016/j.drudis.2021.06.008]. Between 2005 and 2006, several DNA vaccines were developed for non-human animal populations, including against viruses including a rhabdovirus in fish [@doi:10.3354/dao064013], porcine reproductive and respiratory syndrome virus [@doi:10.2527/2006.843733x], and West Nile virus in horses [@doi:10.2460/javma.2005.226.240]. Within the past five years, additional plasmid-vectored vaccines for immunization against viruses were developed against a herpesvirus (in mice) [@doi:10.1089/vim.2020.0082] and an alphavirus (in fish) [@doi:10.1016/j.fsi.2018.07.012].

7) The reference list does not follow the format required by mSystems. In particular, volume and page # are missing.

The change has been made.

**Note: the 8th reviewer comment needs to be handled in a separte PR that I will link here!**

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13af8b15f470`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.