# Issue

**Title:** Only split the SH off UNITE species labels that end in one

## Description

.

`convert_sintax_output.py` split the last `_...` off every UNITE species label as the SH. UNITE 10 labels don't have one (`s:Fusarium_oxysporum`), so the epithet ended up in the SH column. I checked the UTAX files we download: none of the 49,245 v10 sequences with a species label have an SH on it, and all 40,671 in 8.2 do (`..._SH1140861.08FU`).

Now the SH is only split off when the label ends in an SH ID like `_SH1140861.08FU`, otherwise the full name is kept and SH is left empty. There was no test for this module, so I added one covering a v10 label, an 8.2 label, a label with more than one underscore (`..._var._alba`) and a hit with no species.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] `CHANGELOG.md` is updated.

This was AI-assisted (Claude Code). I've gone through all the changes and test runs myself and understand them.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27bbb2eaa0e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.