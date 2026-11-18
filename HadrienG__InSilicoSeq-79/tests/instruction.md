# Issue

**Title:** Bump biopython from 1.72 to 1.73

## Description

Bumps [biopython](https://github.com/biopython/biopython) from 1.72 to 1.73.
<details>
<summary>Changelog</summary>

*Sourced from [biopython's changelog](https://github.com/biopython/biopython/blob/master/NEWS.rst).*

> 18 December 2018: Biopython 1.73
> ================================
>
> This release of Biopython supports Python 2.7, 3.4, 3.5, 3.6 and 3.7.
> It has also been tested on PyPy2.7 v6.0.0 and PyPy3.5 v6.0.0.
>
> As in recent releases, more of our code is now explicitly available under
> either our original "Biopython License Agreement", or the very similar but
> more commonly used "3-Clause BSD License".  See the ``LICENSE.rst`` file for
> more details.
>
> The dictionary-like indexing in SeqIO and SearchIO will now explicitly preserve
> record order to match a behaviour change in the Python standard dict object.
> This means looping over the index will load the records in the on-disk order,
> which will be much faster (previously it would be effectively at random, based
> on the key hash sorting).
>
> The "grant" matrix in Bio.SubsMat.MatrixInfo has been replaced as our original
> values taken from Gerhard Vogt's old webpages at EMBL Heidelberg were
> discovered to be in error. The new values have been transformed following
> Vogt's approach, taking the global maximum 215 minus the similarity scores
> from the original paper Grantham (1974), to give a distance measure.
>
> Additionally, a number of small bugs and typos have been fixed with further
> additions to the test suite, and there has been further work to follow the
> Python PEP8, PEP257 and best practice standard coding style.
>
> Double-quote characters in GenBank feature qualifier values in ``Bio.SeqIO``
> are now escaped as per the NCBI standard. Improperly escaped values trigger a
> warning on parsing.
>
> There is a new command line wrapper for the BWA-MEM sequence mapper.
>
> The string-based FASTA parsers in ``Bio.SeqIO.FastaIO`` have been optimised,
> which also speeds up parsing FASTA files using ``Bio.SeqIO.parse()``.
>
> Many thanks to the Biopython developers and community for making this release
> possible, especially the following contributors:
>
> - Alona Levy-Jurgenson (first contribution)
> - Ariel Aptekmann
> - Brandon Invergo
> - Catherine Lesuisse
> - Chris Rands
> - Darcy Mason (first contribution)
> - Devang Thakkar (first contribution)
> - Ivan Antonov (first contribution)
> - Jeremy LaBarage (first contribution)
> - Juraj Szász (first contribution)
> - Kai Blin
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

- See full diff in [compare view](https://github.com/biopython/biopython/commits)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=biopython&package-manager=pip&previous-version=1.72&new-version=1.73)](https://dependabot.com/compatibility-score.html?dependency-name=biopython&package-manager=pip&previous-version=1.72&new-version=1.73)

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