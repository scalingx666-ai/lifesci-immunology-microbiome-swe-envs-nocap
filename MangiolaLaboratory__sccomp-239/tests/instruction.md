# Issue

**Title:** Add package-level help documentation

## Description

Adds package-level help page following R package conventions, as demonstrated by the DESeq2 example.

## Changes

- **R/sccomp-package.R** - Roxygen2 documentation block using `"_PACKAGE"` marker with package description, main function references, citation, and GitHub links
- **man/sccomp-package.Rd** - Generated help file accessible via `?sccomp` or `help(package="sccomp")`

## Usage

```r
# Access package help
?sccomp
help(package="sccomp")
```

The help page lists core functions (`sccomp_estimate`, `sccomp_test`, `sccomp_predict`, etc.), references the PNAS 2023 publication, and links to vignettes and GitHub resources.

<!-- START COPILOT CODING AGENT SUFFIX -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>create a package help man page</issue_title>
> <issue_description>take this example
>
> https://github.com/thelovelab/DESeq2/blob/5337ba15ae6e9c9aaa1874f088a96c6eb8ccef72/man/DESeq2-package.Rd#L6</issue_description>
>
> <agent_instructions>take this example
>
> https://github.com/thelovelab/DESeq2/blob/5337ba15ae6e9c9aaa1874f088a96c6eb8ccef72/man/DESeq2-package.Rd#L6</agent_instructions>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

- Fixes MangiolaLaboratory/sccomp#238

<!-- START COPILOT CODING AGENT TIPS -->
---

💬 We'd love your input! Share your thoughts on Copilot coding agent in our [2 minute survey](https://gh.io/copilot-coding-agent-survey).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6f2afe04ce0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.