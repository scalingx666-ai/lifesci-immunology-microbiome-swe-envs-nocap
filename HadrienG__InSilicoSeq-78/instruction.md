# Issue

**Title:** Bump pysam from 0.15.1 to 0.15.2

## Description

Bumps [pysam](https://github.com/pysam-developers/pysam) from 0.15.1 to 0.15.2.
<details>
<summary>Release notes</summary>

*Sourced from [pysam's releases](https://github.com/pysam-developers/pysam/releases).*

> ## pysam-0.15.2
> Bugfix release.
> 
> * [#746] catch pileup itorator out-of-scope segfaults
> * [#747] fix faixd fetch with region
> * [#748] increase max_pos to (1<<31)-1
> * [#645] Add missing macOS stub files in `MANIFEST.in`, [**SoapZA**](https://github.com/SoapZA)
> * [#737] Fix bug in get_aligned_pairs, [**bkohrn**](https://github.com/bkohrn)
</details>
<details>
<summary>Changelog</summary>

*Sourced from [pysam's changelog](https://github.com/pysam-developers/pysam/blob/master/NEWS).*

> Release 0.15.2
> ==============
>
> Bugfix release.
>
> * [#746] catch pileup itorator out-of-scope segfaults
> * [#747] fix faixd fetch with region
> * [#748] increase max_pos to (1<<31)-1
> * [#645] Add missing macOS stub files in `MANIFEST.in`, [**SoapZA**](https://github.com/SoapZA)
> * [#737] Fix bug in get_aligned_pairs, [**bkohrn**](https://github.com/bkohrn)
</details>
<details>
<summary>Commits</summary>

-  Merge pull request  from nsoranzo/remove_sudo_false
-  {AH} update release notes
-  {AH} catch pileup itorator out-of-scope segfaults,
-  Remove deprecated sudo: false from .travis.yml
-  Merge pull request  from pysam-developers/AH-fix-faidx-fetch-with-region
-  {AH} update test case for aligned_ref, see issue
-  Merge branch 'bkohrn-master'
-  {AH} add test case for aligned_ref, see issue
-  Merge branch 'master' of https://github.com/bkohrn/pysam into bkohrn-master
-  {AH} fix faixd fetch with region,
- Additional commits viewable in [compare view](https://github.com/pysam-developers/pysam/compare/v0.15.1...v0.15.2)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=pysam&package-manager=pip&previous-version=0.15.1&new-version=0.15.2)](https://dependabot.com/compatibility-score.html?dependency-name=pysam&package-manager=pip&previous-version=0.15.1&new-version=0.15.2)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

**Note:** This repo was added to Dependabot recently, so you'll receive a maximum of 5 PRs for your first few update runs. Once an update run creates fewer than 5 PRs we'll remove that limit.

You can always request more updates by clicking `Bump now` in your [Dependabot dashboard](https://app.dependabot.com).

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot ignore this [patch|minor|major] version` will close this PR and stop Dependabot creating any more for this minor/major version (unless you reopen the PR or upgrade to it yourself)
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `176162474a84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.