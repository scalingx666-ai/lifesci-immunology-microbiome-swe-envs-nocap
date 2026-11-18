# Issue

**Title:** Fixup: PR 811: install an upper-bounded version of Jinja2 during documentation build

## Description

I'm hopeful that this will resolve the continuous integration failure in #811.

It looks like the [`ImportError: cannot import name 'environmentfilter' from 'jinja2'` error seen in the build logs there](https://github.com/biocore/emperor/actions/runs/3915643613/jobs/6694009088#step:9:24) is a symptom of using some less-recent versions of `sphinx` (as packaged with stable/LTS Ubuntu versions) with quite-recent versions of `Jinja2` -- particularly v3.1.0 of `Jinja2` and beyond.

Until a recent-enough version of `sphinx` is available in the `ubuntu-latest` GitHub runner image, it should be possible to install an upper-bounded version of `Jinja2` as a workaround.

- Ref: 

- Ref: 

(please note: this pull request is opened against the master branch instead of the #811 pull request branch so that it is [eligible for continuous integration](https://github.com/biocore/emperor/blob/851154e886efd95ce28f54267f19aecbe2a95188/.github/workflows/main.yml#L7-L8) -- but it's intended to be merged into #811)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `851154e886ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.