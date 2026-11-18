# Issue

**Title:** Some (mostly coloring-focused) bug fixes

## Description

and . Also fixes that `naturalSort()` Infinity issue we talked about (there isn't an open issue for that though).

The JavaScript tests have ~~mostly~~ all been updated. This involved updating both the expected colors from the interpolation fixes, as well as updating slightly different colors due to the new Chroma.js version. (For the two tests that directly checked gradient SVG equality, I elected to just copy in the new expected SVG over the old expected SVG markup -- changing each hex color manually seemed kinda daunting, as shown in the QUnit diff below.)

![errors](https://user-images.githubusercontent.com/4177727/81612522-d4ec0500-9391-11ea-9fcd-641bfea99cd2.png)

I also tested this manually, and can confirm that this  -- see below, where the interpolated Viridis colors now extend to cover the full color map.

![image](https://user-images.githubusercontent.com/4177727/81614561-1500b700-9395-11ea-897d-129ac8770bc7.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `023b6ecb761c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.