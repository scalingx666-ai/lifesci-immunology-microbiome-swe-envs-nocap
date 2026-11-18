# Issue

**Title:** Bump pysam from 0.15.2 to 0.15.3

## Description

Bumps [pysam](https://github.com/pysam-developers/pysam) from 0.15.2 to 0.15.3.
<details>
<summary>Release notes</summary>

*Sourced from [pysam's releases](https://github.com/pysam-developers/pysam/releases).*

> ## pysam-v0.15.3
> Release 0.15.3
> ==============
> 
> Bugfix release.
> 
> *  allow reading of UTF-8 encoded text in VCF/BCF files.
> *  close all filehandles before opening new ones in pysam_dispatch
> *  do not cache VariantRecord.id to avoid memory leak
> *  default of multiple_iterators=True is changed to False for
>   CRAM files.
> *  fix collections.abc import
> *  use bcf_hdr_format instead of bcf_hdr_fmt_text, fix memcpy
>   bug when setting FORMAT fields.
> *  Use HTSlib's kstring_t, which reallocates and enlarges its
>   memory as needed, rather than a fixed-size char buffer.
> *  Build wheels and upload them to PyPI
> *  Allow passing flags and arguments to index methods
> *  Strip \0 in header check
> *  Test Tabix index contents, not the compression
</details>
<details>
<summary>Changelog</summary>

*Sourced from [pysam's changelog](https://github.com/pysam-developers/pysam/blob/master/NEWS).*

> Release 0.15.3
> ==============
>
> Bugfix release.
>
> *  allow reading of UTF-8 encoded text in VCF/BCF files.
> *  close all filehandles before opening new ones in pysam_dispatch
> *  do not cache VariantRecord.id to avoid memory leak
> *  default of multiple_iterators=True is changed to False for
>   CRAM files.
> *  fix collections.abc import
> *  use bcf_hdr_format instead of bcf_hdr_fmt_text, fix memcpy
>   bug when setting FORMAT fields.
> *  Use HTSlib's kstring_t, which reallocates and enlarges its
>   memory as needed, rather than a fixed-size char buffer.
> *  Build wheels and upload them to PyPI
> *  Allow passing flags and arguments to index methods
> *  Strip \0 in header check
> *  Test Tabix index contents, not the compression
</details>
<details>
<summary>Commits</summary>

-  Merge pull request  from jmarshall/configure-env
-  Fix Travis build failures due to libdeflate; re-enable Travis lzma
-  Run configure with the correct CC/CFLAGS/LDFLAGS env vars
-  {AH} increase version to 0.15.3
-  {AH} release notes for 0.15.3
-  {AH} set pileup multiple_iterators to False for CRAM and warn, revert to True...
-  Merge pull request  from pysam-developers/AH-fix-cpy-error
-  {AH} add username and secret to .travis.yml
-  Merge pull request  from pysam-developers/tneymanov-unicode
-  Merge pull request  from nsoranzo/wheels
- Additional commits viewable in [compare view](https://github.com/pysam-developers/pysam/compare/v0.15.2...v0.15.3)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=pysam&package-manager=pip&previous-version=0.15.2&new-version=0.15.3)](https://dependabot.com/compatibility-score.html?dependency-name=pysam&package-manager=pip&previous-version=0.15.2&new-version=0.15.3)

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
- `@dependabot ignore this [patch|minor|major] version` will close this PR and stop Dependabot creating any more for this minor/major version (unless you reopen the PR or upgrade to it). To ignore the version in this PR you can just close it
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a6a0ab0fcf2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.