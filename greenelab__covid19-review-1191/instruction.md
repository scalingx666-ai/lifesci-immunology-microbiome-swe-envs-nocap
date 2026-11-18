# Issue

**Title:** Response to reviewer suggestions for reorg of subunit vaccines

## Description

<!-- Hi there! Please use the template below as a guide for opening a pull request.
This template is designed to help the pull request process go smoother.
If anything doesn't make sense to you, please open the pull request anyway and leave entries blank as needed.
Thank you for your contribution!! -->

### Description of the proposed additions or changes
<!-- If the additions or changes aren't self explanatory feel free to leave a description or notes here. -->

- [x] 1.6 Sections 6.2 and 6.3 (starting from Line 465): While in section 5.1, authors provided more thorough reviews and went over many different IWV-based COVID-19 vaccines, only two specific subunit vaccines, Nuvaxoid and Covifenz, were mentioned. Please consider including more subunit vaccines in Table 2 in the paragraphs and make them concise, as needed. This change may also impact Section 6.4, so please update Section 6.4 accordingly.
- [x] 3.1 The manuscript is subdivided into sections and sub-sections with headings and subheadings, respectively. Please ensure that the text under each subsection is reflecting the heading/subheading and that the information the reader intuitively seeks for under a specific heading is included in that heading. 
- [x] If such information/data are not or not yet available, I would recommend mentioning the lack of such. For example(s), certain sections such as 6.4 the authors revisit clinical trials of Novavax and do not discuss safety.
- [x] Please make the distinctions between trials and real-world data clear throughout the manuscript.
- [x] 3.2 As I understood, the authors generally aim to discuss the platform, dose/regimen, clinical trial efficacy and safety data in sections named Application to COVID-19 or ones with vaccine name (Covifenz, Nuvaxovid) and then RW effectiveness, safety and response/implications for VoC under sections named Real-World Safety and Efficacy. I would first suggest using a uniform naming system for different platforms. Some Real-World Safety and Efficacy sections go back to clinical trials and overview VoC, some are entirely dedicated to VoC. You could add VoC to the subheadings or, as with live attenuated vaccines section, have a separate subsection devoted to VoC, as large part of VoC-related text represents immune outcome data, not RWE per se. With, for example, CoronaVac, the real-world data from Chile is addressed in the more general section and not mentioned in the RW Safety and Efficacy section. As above, I would recommend clearly separating the source of data (trial vs real-world). Also, I suggest logically structuring the RW Safety and Efficacy section as follows: first - effectiveness data (or lack of such) shortly following vaccination, over time, as related to boosters, as pertaining to the VoC.
- [x] 3.3 The authors discuss efficacy/effectiveness, side effect profile, sometimes regulatory details for most of the vaccines. Please make sure each of these outcomes are addressed for each vaccine. For example, RW safety and effectiveness information is lacking for IWV vaccines section, while all of them discuss VoC. Similarly, **safety and side effect details are not provided for Nuvaxovid, for example**. As above, I recommend ensuring the data points given for each platform/vaccine are uniform; separating immune outcome data from the real-world effectiveness; mentioning the lack of data wherever relevant.
- [x] 3.6 When providing percent-efficacy or effectiveness, I recommend to consistently indicate the time period/interval over which the outcome is reported (already included in many cases).
- [x] 3.7 I would suggest using the same naming for vaccines after they (and their alternative names) are first mentioned. For example, Covilo and Sinopharm, CoronaVac and Sinovac are used interchangeably, and it can be confusing for some readers.
- [x] 3.9 Please make sure all relevant sentences are followed by a reference, where appropriate, e.g. (not limited to) lines 143, 191, **469**.
- [x] 3.30 Lines 409-411 are identical to lines 415-417, please leave where more appropriate.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b591070a91f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.