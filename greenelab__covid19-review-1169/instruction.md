# Issue

**Title:** Additional template variables for vaccines manuscripts

## Description

<!-- Hi there! Please use the template below as a guide for opening a pull request.
This template is designed to help the pull request process go smoother.
If anything doesn't make sense to you, please open the pull request anyway and leave entries blank as needed.
Thank you for your contribution!! -->

### Description of the proposed additions or changes
<!-- If the additions or changes aren't self explanatory feel free to leave a description or notes here. -->
There were a few notes in the vaccines manuscripts to add template variables that were not generated. 

This PR adds:
- owid_total_countries: a count of the total number of countries with vaccine data in OWID's dataset
- viper_date_pretty: extracts the date of last update from the HTML on the viper site
- Sinovac_country_count: the number of countries for which Sinovac Coronavac distribution data is available
- Sinovac_continents: a string indicating the names of the continents where Sinovac Coronavac is distributed (formatted as "X, Y, and Z")
- Covaxin_country_count: the number of countries for which Covaxin distribution data is available
- Covaxin_continents: a string indicating the names of the continents where Covaxin is distributed (formatted as "X, Y, and Z")

It also adds a period to the end of the sentences generated saying no approved vaccines in the dataset were developed on a continent

Additionally, all variables in the JSON are now strings (probably doesn't matter, but I hadn't been careful about this, and it seems strategic for the sake of future sanity...)

### Related issues
<!-- GitHub will link issues to pull requests if you list the related issue numbers like "#2, #17". -->
#1167 

### Suggested reviewers (optional)
<!-- If there are particular people you think should review this pull request, please list their GitHub handle like "@rando2".-->


### Checklist
<!-- Please mark the following tasks as complete by putting an "x" in the box like "[x]".
If a particular item is not applicable to your pull request, please delete the item. -->
- [ ] Text is formatted so that each sentence is on its own line.
<!-- see why this is recommended here:https://github.com/greenelab/covid19-review/blob/627a5f45a2d1fcb2150d1466df63bb848f22a3d4/USAGE.md#manubot-markdown -->
- [ ] Pre-prints cited in this pull request have a GitHub issue opened so that they can be reviewed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7ef4c04ac8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.