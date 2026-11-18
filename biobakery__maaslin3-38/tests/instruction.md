# Issue

**Title:** move (T)SE to Suggests. check_installed() where needed. Add test to c…

## Description

We welcome feedback and issue reporting for all bioBakery tools through our [Discourse site](https://forum.biobakery.org/c/pull-request/featurepull-request/). For users that would like to directly contribute to the [tools](https://github.com/biobakery/) we are happy to field PRs to address **bug fixes**. Please note the turn around time on our end might be a bit long to field these but that does not mean we don't value the contribution! We currently **don't** accept PRs to add **new functionality** to tools but we would be happy to receive your feedback on [Discourse](https://forum.biobakery.org/c/pull-request/featurepull-request/).

Also, we will make sure to attribute your contribution in our User’s manual(README.md) and in any associated paper Acknowledgements.


## Description

This PR:

* moves `TreeSummarizedExperiment` and `SummarizedExperiment` to Suggests
* checks if the necessary packages are installed with `rlang::check_installed()` in the corresponding reader function when the user passes in an SE
* Adds a test for reading SEs

I discussed this change with Will over Slack. This lowers the number of required dependencies from 102 to 64 and lowers the time required to attach the package (`system.time({library(maaslin3)})`) from 4.686s to 0.734s (on my system).

```r
havel::plot_deps_graph("biobakery/MaAsLin3@0071631")
```

<img width="960" height="720" alt="m3_bb" src="https://github.com/user-attachments/assets/bbfdad06-64de-4525-a073-d393c5a91b12" />

```r
havel::plot_deps_graph("andrewGhazi/MaAsLin3@suggestSE")
```

<img width="960" height="720" alt="m3_no_SE" src="https://github.com/user-attachments/assets/ff36dca2-16c7-41bd-b3c8-16f8587c7eac" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `007163199924`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.