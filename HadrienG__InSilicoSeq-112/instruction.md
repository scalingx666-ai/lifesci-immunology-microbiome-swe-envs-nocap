# Issue

**Title:** Bump scipy from 1.3.0 to 1.3.1

## Description

Bumps [scipy](https://github.com/scipy/scipy) from 1.3.0 to 1.3.1.
<details>
<summary>Release notes</summary>

*Sourced from [scipy's releases](https://github.com/scipy/scipy/releases).*

> ## SciPy 1.3.1
> SciPy `1.3.1` is a bug-fix release with no new features compared to `1.3.0`.
> 
> Authors
> =======
> 
> * Matt Haberland
> * Geordie McBain
> * Yu Feng
> * Evgeni Burovski
> * Sturla Molden
> * Tapasweni Pathak
> * Eric Larson
> * Peter Bell
> * Carlos Ramos Carreño +
> * Ralf Gommers
> * David Hagen
> * Antony Lee
> * Ayappan P
> * Tyler Reddy
> * Pauli Virtanen
> 
> A total of 15 people contributed to this release.
> People with a "+" by their names contributed a patch for the first time.
> This list of names is automatically generated, and may not be fully complete.
</details>
<details>
<summary>Commits</summary>

-  REL: SciPy 1.3.1 release commit
-  Merge pull request  from tylerjereddy/131_prep
-  MAINT, DOC: update 1.3.1 release notes
-  BUG: interpolate: fix broken conversions between PPoly/BPoly objects
-  Fix 5040
-  DOC: reconstruct SuperLU permutation matrices in one step
-  BUG: optimize: wrap ma.mask, which could be 0d, in np.atleast_1d
-  BUG: optimize: dummy commit to investigate  on CI
-  Move ascontiguousarray higher.
-  Fix error on discontiguous ckdtree.query_ball_point input.
- Additional commits viewable in [compare view](https://github.com/scipy/scipy/compare/v1.3.0...v1.3.1)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=scipy&package-manager=pip&previous-version=1.3.0&new-version=1.3.1)](https://dependabot.com/compatibility-score.html?dependency-name=scipy&package-manager=pip&previous-version=1.3.0&new-version=1.3.1)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language
- `@dependabot badge me` will comment on this PR with code to add a "Dependabot enabled" badge to your readme

Additionally, you can set the following in your Dependabot [dashboard](https://app.dependabot.com):
- Update frequency (including time of day and day of week)
- Automerge options (never/patch/minor, and dev/runtime dependencies)
- Pull request limits (per update run and/or open at any time)
- Out-of-range updates (receive only lockfile updates, if desired)
- Security updates (receive only security updates, if desired)

Finally, you can contact us by mentioning @dependabot.

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `823b57bcb2a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.