# Issue

**Title:** Automatically resize main legend when changing tree coloring

## Description

The main legend in the application is resizable, and its size will automatically change as the tree is colored by different categories. However, this behavior currently stops working after the user manually resizes the legend at all:

![leg](https://user-images.githubusercontent.com/4177727/116769612-39b0cd00-a9f2-11eb-9cd3-21868265dfa6.gif)

We should keep the ability for users to manually resize the legend, IMO, since the legend can get really large and we don't want it to obstruct the user's view.

It looks like the reason for this is that, when the user manually resizes the legend, that the `width` / `height` attributes of the legend go from being unspecified to being fixed: (note the `element.style` text in the dev console on the right)

![wh](https://user-images.githubusercontent.com/4177727/116769668-94e2bf80-a9f2-11eb-86eb-493d3661acb1.gif)

This PR fixes this, by resetting the width/height of the main legend to their defaults right before we adjust tree coloring:

![Peek 2021-04-30 20-53](https://user-images.githubusercontent.com/4177727/116770129-34558180-a9f6-11eb-82ee-efc9d7da92f3.gif)

It's worth noting that this PR will need to be updated once #484 is merged in so that `Empress.resizeLegend()` is called before creating a continuous legend.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b8a340bbff0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.