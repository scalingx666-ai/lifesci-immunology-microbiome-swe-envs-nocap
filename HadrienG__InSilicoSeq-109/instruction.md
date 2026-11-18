# Issue

**Title:** Bump biopython from 1.73 to 1.74

## Description

Bumps [biopython](https://github.com/biopython/biopython) from 1.73 to 1.74.
<details>
<summary>Changelog</summary>

*Sourced from [biopython's changelog](https://github.com/biopython/biopython/blob/master/NEWS.rst).*

> 16 July 2019: Biopython 1.74
> ============================
>
> This release of Biopython supports Python 2.7, 3.4, 3.5, 3.6 and 3.7. However, it will be the last release to support Python 3.4 which is now at end-of-life. It has also been tested on PyPy2.7 v6.0.0 and PyPy3.5 v6.0.0.
>
> As in recent releases, more of our code is now explicitly available under either our original "Biopython License Agreement", or the very similar but more commonly used "3-Clause BSD License". See the `LICENSE.rst` file for more details.
>
> Our core sequence objects (`Seq`, `UnknownSeq`, and `MutableSeq`) now have a string-like `.join()` method.
>
> The NCBI now allows longer accessions in the GenBank file LOCUS line, meaning the fields may not always follow the historical column based positions. We no longer give a warning when parsing these. We now allow writing such files (although with a warning as support for reading them is not yet widespread).
>
> Support for the `mysqlclient` package, a fork of MySQLdb, has been added.
>
> We now capture the IDcode field from PDB Header records.
>
> `Bio.pairwise2`'s pretty-print output from `format_alignment` has been optimized for local alignments: If they do not consist of the whole sequences, only the aligned section of the sequences are shown, together with the start positions of the sequences (in 1-based notation). Alignments of lists will now also be prettily printed.
>
> `Bio.SearchIO` now supports parsing the text output of the HHsuite protein sequence search tool. The format name is `hhsuite2-text` and `hhsuite3-text`, for versions 2 and 3 of HHsuite, respectively.
>
> `Bio.SearchIO` HSP objects has a new attribute called `output_index`. This attribute is meant for capturing the order by which the HSP were output in the parsed file and is set with a default value of -1 for all HSP objects. It is also used for sorting the output of `QueryResult.hsps`.
>
> `Bio.SeqIO.AbiIO` has been updated to preserve bytes value when parsing. The goal of this change is make the parser more robust by being able to extract string-values that are not utf-8-encoded. This affects all tag values, except for ID and description values, where they need to be extracted as strings to conform to the `SeqRecord` interface. In this case, the parser will attempt to decode using `utf-8` and fall back to the system encoding if that fails. This change affects Python 3 only.
>
> `Bio.motifs.mast` has been updated to parse XML output files from MAST over the plain-text output file. The goal of this change is to parse a more structured data source with minimal loss of functionality upon future MAST releases. Class structure remains the same plus an additional attribute `Record.strand_handling` required for diagram parsing.
>
> `Bio.Entrez` now automatically retries HTTP requests on failure. The maximum number of tries and the sleep between them can be configured by changing `Bio.Entrez.max_tries` and `Bio.Entrez.sleep_between_tries`. (The defaults are 3 tries and 15 seconds, respectively.)
>
> All tests using the older print-and-compare approach have been replaced by unittests following Python's standard testing framework.
>
> On the documentation side, all the public modules, classes, methods and functions now have docstrings (built in help strings). Furthermore, the PDF version of the *Biopython Tutorial and Cookbook* now uses syntax coloring for code snippets.
>
> Additionally, a number of small bugs and typos have been fixed with further additions to the test suite, and there has been further work to follow the Python PEP8, PEP257 and best practice standard coding style.
>
> Many thanks to the Biopython developers and community for making this release possible, especially the following contributors:
>
> -   Andrey Raspopov (first contribution)
> -   Antony Lee
> -   Benjamin Rowell (first contribution)
> -   Bernhard Thiel
> -   Brandon Invergo
> -   Catherine Lesuisse
> -   Chris Rands
> -   Deepak Khatri (first contribution)
> -   Gert Hulselmans
> -   Jared Andrews
> -   Jens Thomas (first contribution)
> -   Konstantin Vdovkin
> -   Lenna Peterson
> -   Mark Amery
> -   Markus Piotrowski
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

- See full diff in [compare view](https://github.com/biopython/biopython/commits)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=biopython&package-manager=pip&previous-version=1.73&new-version=1.74)](https://dependabot.com/compatibility-score.html?dependency-name=biopython&package-manager=pip&previous-version=1.73&new-version=1.74)

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