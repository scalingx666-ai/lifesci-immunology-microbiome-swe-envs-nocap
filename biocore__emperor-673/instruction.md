# Issue

**Title:** Use shaders to render hundreds of thousands of samples with a responsive UI

## Description

## TL;DR: here's a responsive plot with [all the public samples from Qiita](https://view.qiime2.org/visualization/?type=html&src=https%3A%2F%2Fdl.dropbox.com%2Fs%2Fp6j6ydlicq9tc53%2Fgotta-go-fast.qzv%3Fdl%3D1).

This PR adds a **fast way** 🔥  to render large datasets and make the UI responsive. In order to do this we move away from using individual geometries per sample and instead use a point cloud or "particle cloud" to render all the samples in a single geometry. As it stands this mode will automatically activate when there's more than 20,000 samples (we can change this to something else).

To do this I implemented a custom shader that draws each sample as a circle, overall this works well since the density of data with large datasets doesn't require a high-level of detail per sample.

By using shaders we are limited on a few respects:
- The shapes controller is disabled, since drawing custom shapes would require a fair amount of shader code.
- Exporting as ~~PNG or~~ SVG is currently not supported since we are using a custom shader and shaders are not supported by ~~these renderers~~ this renderer.
- We can't use jackknifed plots.

While this PR is large, most of the changes are test code. Most of the relevant changes are in view.js. I implemented a few convenience setters for the visual attributes (color, size, etc) and added `_fastInit` to create the shader-based geometry.

---------

The ordination is courtesy of @wasade 🎩

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `424271c4a147`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.