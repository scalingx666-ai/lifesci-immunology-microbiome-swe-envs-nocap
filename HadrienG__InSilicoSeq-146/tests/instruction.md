# Issue

**Title:** Bump pysam from 0.15.3 to 0.15.4

## Description

Bumps [pysam](https://github.com/pysam-developers/pysam) from 0.15.3 to 0.15.4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pysam-developers/pysam/releases">pysam's releases</a>.</em></p>
<blockquote>
<h2>pysam-v0.15.4</h2>
<h1>Release 0.15.4</h1>
<p>Bugfix release. Principal reason for release is to update cython
version in order to fix pip install pysam with python 3.8.</p>
<ul>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/879">#879</a> Fix add_meta function in libcbcf.pyx, so meta-information
lines in header added with this function have double-quoting rules
in accordance to rules specified in VCF4.2 and VCF4.3 specifications</li>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/863">#863</a> Force arg to bytes to support non-ASCII encoding</li>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/875">#875</a> Bump minimum Cython version</li>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/868">#868</a> Prevent segfault on Python 2.7 AlignedSegment.compare(other=None)</li>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/867">#867</a> Fix wheel building on TravisCI</li>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/863">#863</a> Force arg to bytes to support non-ASCII encoding</li>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/799">#799</a> disambiguate interpretation of bcf_read return code</li>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/841">#841</a> Fix silent truncation of FASTQ with bad q strings</li>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/846">#846</a> Prevent segmentation fault on ID, when handling malformed records</li>
<li><a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/829">#829</a> Run configure with the correct CC/CFLAGS/LDFLAGS env va</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pysam-developers/pysam/blob/master/NEWS">pysam's changelog</a>.</em></p>
<blockquote>
<p>An online version of the installation instructions can be found here:
<a href="http://pysam.readthedocs.io/en/latest/release.html">http://pysam.readthedocs.io/en/latest/release.html</a></p>
<h1>=============
Release notes</h1>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c818db5</code></a> {AH} import utils with package name</li>
<li><a href=""><code>9ff3144</code></a> {AH} add release notes and bump version to 0.15.4</li>
<li><a href=""><code>44fc853</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/879">#879</a> from lltw/fix-add-meta-in-variant-header-class</li>
<li><a href=""><code>9225acc</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/878">#878</a> from nsoranzo/patch-1</li>
<li><a href=""><code>b6b5ce6</code></a> Restore twine upload on tag</li>
<li><a href=""><code>bafb0e9</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/875">#875</a> from ExplodingCabbage/bump-min-cython</li>
<li><a href=""><code>74fa4ef</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/868">#868</a> from rjlasko/AlignedSegment-compare-None</li>
<li><a href=""><code>6b2dddd</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/867">#867</a> from nsoranzo/wheels</li>
<li><a href=""><code>75df608</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/866">#866</a> from amblina/amblina-patch-1</li>
<li><a href=""><code>2f84777</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pysam-developers/pysam/issues/863">#863</a> from codeunsolved/fix-libcutils-encoding</li>
<li>Additional commits viewable in <a href="https://github.com/pysam-developers/pysam/compare/v0.15.3...v0.15.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=pysam&package-manager=pip&previous-version=0.15.3&new-version=0.15.4)](https://dependabot.com/compatibility-score.html?dependency-name=pysam&package-manager=pip&previous-version=0.15.3&new-version=0.15.4)

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
- Pull request limits (per update run and/or open at any time)
- Automerge options (never/patch/minor, and dev/runtime dependencies)
- Out-of-range updates (receive only lockfile updates, if desired)
- Security updates (receive only security updates, if desired)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `03bfa5a5a2e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.