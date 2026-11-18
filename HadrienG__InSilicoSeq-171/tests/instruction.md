# Issue

**Title:** Bump biopython from 1.76 to 1.77

## Description

Bumps [biopython](https://github.com/biopython/biopython) from 1.76 to 1.77.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/biopython/biopython/blob/master/NEWS.rst">biopython's changelog</a>.</em></p>
<blockquote>
<h1>25 May 2020: Biopython 1.77</h1>
<p>This release of Biopython supports Python 3.6, 3.7 and 3.8 It has also been tested on PyPy3.6.1 v7.1.1-beta0.</p>
<p><strong>We have dropped support for Python 2 now.</strong></p>
<p><code>pairwise2</code> now allows the input of parameters with keywords and returns the alignments as a list of <code>namedtuples</code>.</p>
<p>The codon tables have been updated to NCBI genetic code table version 4.5, which adds Cephalodiscidae mitochondrial as table 33.</p>
<p>Updated <code>Bio.Restriction</code> to the January 2020 release of REBASE.</p>
<p>A major contribution by Rob Miller to <code>Bio.PDB</code> provides new methods to handle protein structure transformations using dihedral angles (internal coordinates). The new framework supports lossless interconversion between internal and cartesian coordinates, which, among other uses, simplifies the analysis and manipulation of coordinates of proteins structures.</p>
<p>As in recent releases, more of our code is now explicitly available under either our original &quot;Biopython License Agreement&quot;, or the very similar but more commonly used &quot;3-Clause BSD License&quot;. See the <code>LICENSE.rst</code> file for more details.</p>
<p>Additionally, a number of small bugs and typos have been fixed with further additions to the test suite. There has been further work to follow the Python PEP8, PEP257 and best practice standard coding style, and more of the code style has been reformatted with the <code>black</code> tool.</p>
<p>Many thanks to the Biopython developers and community for making this release possible, especially the following contributors:</p>
<ul>
<li>Alexander Decurnou (first contribution)</li>
<li>Andrei Istrate (first contribution)</li>
<li>Andrey Raspopov</li>
<li>Austin Varela (first contribution)</li>
<li>Chris Daley</li>
<li>Chris Rands</li>
<li>Deepak Khatri</li>
<li>Hielke Walinga (first contribution)</li>
<li>Kai Blin</li>
<li>Karthikeyan Singaravelan (first contribution)</li>
<li>Markus Piotrowski</li>
<li>Michiel de Hoon</li>
<li>Peter Cock</li>
<li>Rob Miller</li>
<li>Sergio Valqui</li>
<li>Steve Bond</li>
<li>Sujan Dulal (first contribution)</li>
<li>Tianyi Shi (first contribution)</li>
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

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=biopython&package-manager=pip&previous-version=1.76&new-version=1.77)](https://dependabot.com/compatibility-score/?dependency-name=biopython&package-manager=pip&previous-version=1.76&new-version=1.77)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27a4c4cc40e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.