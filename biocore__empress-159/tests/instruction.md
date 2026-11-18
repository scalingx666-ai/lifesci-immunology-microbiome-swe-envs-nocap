# Issue

**Title:** Handle categorical colorschemes correctly; add tests for colorer.js; fix a tiny bug

## Description

.

### Summary
This PR changes `colorer.js` so that all colorschemes are treated as categorical, replacing the old behavior of treating all colorschemes as quantitative (). **If desired, I can modify this PR (or we can open an issue for later) to support toggling between categorical / quantitative colorschemes;** I wasn't sure if we wanted to focus on that for now, or how the UX for that functionality would work, which is why I'm making this PR sooner rather than later :)

### Other stuff added in this PR

- Fairly comprehensive tests for `colorer.js` (#142).
  - The `addColorsToSelect()` method is still untested (I don't _think_ there are any JS tests yet that create HTML elements for use in tests; I wanted to hold off on testing this for now so I could pick your brains on how best to do this), but the rest of the functions in the class are covered.

- Fixed a minor bug in how RGB colors were computed.
  - Long story short, `Colorer.getColorRGB()` produces an array of `[r, g, b]`, where each of the three  elements in the array is a number in the range `[0, 1]`. As an intermediate step, the code was generating an array of elements in the range `[0, 255]`, but was then converting these to `[0, 1]` by dividing by `256` instead of by `255`.
  - This introduced a small amount of imprecision, since e.g. `#ffffff` would've been converted to `[255, 255, 255]` and then to `[0.996, 0.996, 0.996]` instead of to `[1, 1, 1]`.
  - [At first I fixed this by changing the denominator to `255` instead of `256`](https://github.com/biocore/empress/blob/49941123338ef6f571d208a15b5611dc829ed9ac/empress/support_files/js/colorer.js#L32-L39), and then while I was writing this PR message out I wondered "wait does chroma already have something that does all of this" and then it turned out that yeah it does in [chroma's `color.gl()`](https://gka.github.io/chroma.js/#color-gl) method, so now I feel silly :sweat_smile: **Edit: see comment below about this method**
  - Anyway, now that `getColorRGB()` is tested, we shouldn't need to worry about this bug again.

### Screenshots

#### Default QIIME colorscheme, coloring by body site

![image](https://user-images.githubusercontent.com/4177727/80178563-5fbbba00-85b3-11ea-8d66-7a2b5ee73731.png)

#### Accent colorscheme, coloring by barcode sequence

This demonstrates the "looping" feature, where (when the number of categories for a metadata field is greater than the number of colors in the palette) things "loop" around.

![image](https://user-images.githubusercontent.com/4177727/80178644-985b9380-85b3-11ea-8d73-ba13088180b9.png)

#### Viridis colorscheme, coloring by barcode sequence

This demonstrates that quantitative colorschemes are currently treated the same way as categorical  colorschemes, which results in funky behavior -- the "looping" looks kind of off here. (The reason Viridis loops after 9 "items" is that this is just how the underlying [`chroma.brewer["Viridis"]`](https://gka.github.io/chroma.js/#chroma-brewer) array is structured.)

![image](https://user-images.githubusercontent.com/4177727/80178989-6b5bb080-85b4-11ea-9d75-16e17d41b2b9.png)

This behavior should likely be changed at some point, either by removing the quant color schemes for now, adding some UI elements to toggle between categorical/quantitative color scales and adjusting the code accordingly, or some third option that I feel like I'm forgetting right now.

![image](https://user-images.githubusercontent.com/4177727/80178716-ca6cf580-85b3-11ea-90b4-8bac1176fdf9.png)

Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bd92b3eab6f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.