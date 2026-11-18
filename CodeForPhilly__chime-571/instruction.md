# Issue

**Title:** [model] Extend prefit n_days when fitting for i_day

## Description

# Link to issue

-  

# Changelog entry

- Correct fitting when date_first_hospitalized is unknown and n_days is too low.

---

## <center>Pull Request Checklist</center>

### <center>For Reviewer</center>

- [ ] Submitted under the correct tag
- [x] Runs without error or warning
- [ ] Documentation  revised / included
- [ ] Unit tests included
- [x] Issues referenced
- [ ] Does not create new bugs / issues

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d756c6e662a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.