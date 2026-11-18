# Issue

**Title:** Bump biopython from 1.75 to 1.76

## Description

Bumps [biopython](https://github.com/biopython/biopython) from 1.75 to 1.76.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/biopython/biopython/blob/master/NEWS.rst">biopython's changelog</a>.</em></p>
<blockquote>
<h1>20 December 2019: Biopython 1.76</h1>
<p>This release of Biopython supports Python 2.7, 3.5, 3.6, 3.7 and 3.8. It has also been tested on PyPy2.7.13 v7.1.1 and PyPy3.6.1 v7.1.1-beta0.</p>
<p>We intend this to be our final release supporting Python 2.7 and 3.5.</p>
<p>As in recent releases, more of our code is now explicitly available under either our original &quot;Biopython License Agreement&quot;, or the very similar but more commonly used &quot;3-Clause BSD License&quot;. See the <code>LICENSE.rst</code> file for more details.</p>
<p>In addition to the mainstream <code>x86_64</code> aka <code>AMD64</code> CPU architecture, we now also test every contribution on the <code>ARM64</code>, <code>ppc64le</code>, and <code>s390x</code> CPUs under Linux thanks to Travis CI. Further post-release testing done by Debian and other packagers and distributors of Biopython also covers these CPUs.</p>
<p><code>Bio.motifs.PositionSpecificScoringMatrix.search()</code> method has been re-written: it now applies <code>.calculate()</code> to chunks of the sequence to maintain a low memory footprint for long sequences.</p>
<p>Additionally, a number of small bugs and typos have been fixed with further additions to the test suite. There has been further work to follow the Python PEP8, PEP257 and best practice standard coding style, and more of the code style has been reformatted with the <code>black</code> tool.</p>
<p>Many thanks to the Biopython developers and community for making this release possible, especially the following contributors:</p>
<ul>
<li>Chris Daley (first contribution)</li>
<li>Chris Rands</li>
<li>Christian Brueffer</li>
<li>Ilya Flyamer (first contribution)</li>
<li>Jakub Lipinski (first contribution)</li>
<li>Michael R. Crusoe (first contribution)</li>
<li>Michiel de Hoon</li>
<li>Peter Cock</li>
<li>Sergio Valqui</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/biopython/biopython/commits">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=biopython&package-manager=pip&previous-version=1.75&new-version=1.76)](https://dependabot.com/compatibility-score.html?dependency-name=biopython&package-manager=pip&previous-version=1.75&new-version=1.76)

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