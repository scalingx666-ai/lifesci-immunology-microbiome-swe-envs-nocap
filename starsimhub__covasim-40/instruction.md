# Issue

**Title:** Clean up styles/address accessibility issues

## Description

Related issue: #39 
 
- [ ]  WCAG 4.1.2 - buttons must have discernible text
- [ ]  WCAG 1.3.1, WCAG 3.3.2 - input controls must be associated with their labels
- [ ]  WCAG 1.4.3 - contrast ratio between text and background must meet AA standards
- [ ]  Keyboard navigation - tooltip information should be accessible for non-mouse users

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `674b5c17c846`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.