# Issue

**Title:** Add article sections to pkgdown site

## Description

This is a small change to the package down site. It reorganizes the vignettes and articles into sections. The sections are currently:

- Getting Started
- Interop
- Other Topics

If those names should be changed to something else, or if you don't like the specific groupings I chose, or the order, let me know and I will update!

---

This is how the articles page looks with the sections:

<img width="300" alt="Screenshot 2026-11-11 at 11 31 55 AM" src="https://github.com/user-attachments/assets/1b4e3b3b-55f4-435b-a860-43c29e8e35e1" />

---

And here is the top of the little dropdown:

<img width="300" alt="Screenshot 2026-11-11 at 11 32 18 AM" src="https://github.com/user-attachments/assets/9d4d64f3-220f-4d36-9621-70a4df46cbfb" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b35959cf75d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.