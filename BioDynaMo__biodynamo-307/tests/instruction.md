# Issue

**Title:** Add support for Ubuntu 22.04

## Description

<details>
<summary><b>The BDM PR checklist</b></summary>

First time contributor? Make sure to review our contributing guidelines:
* [Code Quality](https://biodynamo.org/docs/devguide/code_quality/)
* [C++ Style Guide](https://biodynamo.org/docs/devguide/contribute/)

- [ ] **Basics**
  - [x] Code builds locally
  - [x] All unit tests pass locally
  - [ ] Code passes CI
  - [x] No IDE artifacts such as `.DS_Store` files (only relevant source code)
  - [x] If for some reason your code produces artifacts, make sure to update the
        `.gitignore` file
  - [x] No new compiler warnings introduced (treat them as an error)

- [x] **New files**
  - [ ] License header
  - [ ] Include guard
  - [ ] BDM namespace

- [x] **New Code**
  - [ ] All new public, protected, and private classes, methods, data members, 
        and functions have full Doxygen-style documentation in source comments.
        Documentation should include descriptions of member data, function
        arguments and return values, template parameters, and prerequisites for
        calling new functions.
  - [ ] Pointer arguments and return values must specify whether ownership is
        being transferred or lent with the call.
  - [ ] If a method is not thead safe, mark it as such. Generally test if
        threading affects your code (e.g. check if it yields the same results in
        parallel regions with and without `OMP_NUM_THREADS=1`)
  - [ ] Coverage via CI, i.e. new code needs to be tested
  - [ ] Unit tests check function to a sufficient degree (quality of test needs
        to be verified by reviewer)
  - [ ] Code formatted with clang format (see `repository-check` CI)
  - [ ] Follows the 
        [C++ style guide](https://google.github.io/styleguide/cppguide.html)
        (must be checked by reviewer)
  - [ ] Address all (or at least the vast majority) of the code smells flagged
        by `SonarCloud`
  - [ ] New code should not break backward compatibility

- [x] **New dependencies**
  - [ ] New dependencies should ideally be optional, e.g. can be turned off with
        `-Doption=off`
  - [ ] New dependencies must be compatible with the Apache2.0 license
  - [ ] Document in new dependencies on the website

- [x] **New feature**
  - [ ] Update documentation for website (if significant feature)
  - [ ] Consider adding notebook or example showing how to use the new feature

- [x] **New example**
  - [ ] Make sure that the example is checked in the System CIs
  - [ ] Verify that example appears on the website after wards and works
        (if the example showcases a new feature, the GitPod container may have
        to be updated)
  
Merge instructions: Squash merger PRs and remove individual commit messages from
merge commit. Make sure to give credit to all contributors via `Co-authored by`.
Remember to delete the branch after merging.

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfe06c919ad8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.