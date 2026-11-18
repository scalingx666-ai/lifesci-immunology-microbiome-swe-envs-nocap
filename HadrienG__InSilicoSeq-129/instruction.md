# Issue

**Title:** Bump biopython from 1.74 to 1.75

## Description

Bumps [biopython](https://github.com/biopython/biopython) from 1.74 to 1.75.
<details>
<summary>Changelog</summary>

*Sourced from [biopython's changelog](https://github.com/biopython/biopython/blob/master/NEWS.rst).*

> 6 November 2019: Biopython 1.75
> ===============================
>
> This release of Biopython supports Python 2.7, 3.5, 3.6, 3.7 and is expected to work on the soon to be released Python 3.8. It has also been tested on PyPy2.7.13 v7.1.1 and PyPy3.6.1 v7.1.1-beta0.
>
> Note we intend to drop Python 2.7 support in early 2020.
>
> The restriction enzyme list in Bio.Restriction has been updated to the August 2019 release of REBASE.
>
> `Bio.SeqIO` now supports reading and writing files in the native format of Christian Marck's DNA Strider program ("xdna" format, also used by Serial Cloner), as well as reading files in the native formats of GSL Biotech's SnapGene ("snapgene") and Textco Biosoftware's Gene Construction Kit ("gck").
>
> `Bio.AlignIO` now supports GCG MSF mutliple sequence alignments as the "msf" format (work funded by the National Marrow Donor Program).
>
> The main `Seq` object now has string-like `.index()` and `.rindex()` methods, matching the existing `.find()` and `.rfind()` implementations. The `MutableSeq` object retains its more list-like `.index()` behaviour.
>
> The `MMTFIO` class is added that allows writing of MMTF file format files from a Biopython structure object. `MMTFIO` has a similar interface to `PDBIO` and `MMCIFIO`, including the use of a `Select` class to write out a specified selection. This final addition to read/write support for PDB/mmCIF/MMTF in Biopython allows conversion between all three file formats.
>
> Values from mmCIF files are now read in as a list even when they consist of a single value. This change improves consistency and reduces the likelihood of making an error, but will require user code to be updated accordingly.
>
> `Bio.PDB` has been updated to support parsing REMARK 99 header entries from PDB-style Astral files.
>
> A new keyword parameter `full_sequences` was added to `Bio.pairwise2`'s pretty print method `format_alignment` to restore the output of local alignments to the 'old' format (showing the whole sequences including the un-aligned parts instead of only showing the aligned parts).
>
> A new function `charge_at_pH(pH)` has been added to `ProtParam` and `IsoelectricPoint` in `Bio.SeqUtils`.
>
> The `PairwiseAligner` in `Bio.Align` was extended to allow generalized pairwise alignments, i.e. alignments of any Python object, for example three-letter amino acid sequences, three-nucleotide codons, and arrays of integers.
>
> A new module `substitution_matrices` was added to `Bio.Align`, which includes an `Array` class that can be used as a substitution matrix. As the `Array` class is a subclass of a numpy array, mathematical operations can be applied to it directly, and C code that makes use of substitution matrices can directly access the numerical values stored in the substitution matrices. This module is intended as a replacement of `Bio.SubsMat`, which is currently unmaintained.
>
> As in recent releases, more of our code is now explicitly available under either our original "Biopython License Agreement", or the very similar but more commonly used "3-Clause BSD License". See the `LICENSE.rst` file for more details.
>
> Additionally, a number of small bugs and typos have been fixed with further additions to the test suite, and there has been further work to follow the Python PEP8, PEP257 and best practice standard coding style. We have also started to use the `black` Python code formatting tool.
>
> Many thanks to the Biopython developers and community for making this release possible, especially the following contributors:
>
> -   Chris MacRaild
> -   Chris Rands
> -   Damien Goutte-Gattat (first contribution)
> -   Devang Thakkar
> -   Harry Jubb
> -   Joe Greener
> -   Kiran Mukhyala (first contribution)
> -   Konstantin Vdovkin
> -   Mark Amery
> -   Markus Piotrowski
> -   Mike Moritz (first contribution)
> -   Mustafa Anil Tuncel
> -   Nick Negretti
> -   Peter Cock
> -   Peter Kerpedjiev
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

- See full diff in [compare view](https://github.com/biopython/biopython/commits)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=biopython&package-manager=pip&previous-version=1.74&new-version=1.75)](https://dependabot.com/compatibility-score.html?dependency-name=biopython&package-manager=pip&previous-version=1.74&new-version=1.75)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `681ee9625efa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.