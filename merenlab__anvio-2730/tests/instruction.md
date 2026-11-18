# Issue

**Title:** Adding an 'Export SVG' button to the inspect page

## Description

This PR adds a button to export the inspect page as an SVG. The button is at the bottom of the inspect page's settings panel:

<img width="402" height="103" alt="image" src="https://github.com/user-attachments/assets/f08aa700-d6c3-45a4-892b-0ee0407934ea" />

In order to do this, we needed a new function in `charts.js` that would combine all SVG elements of the inspect page (since there are multiple -- the per-sample coverage charts, SNV info, sample labels, gene arrow/context, and any highlights are all separate elements) into one merged SVG before triggering the download. The function explicitly:

- Collects the five SVG layers that make up the inspect page (#chart-container, #highlight-boxes, #SNV-boxes, #sample-titles, #context-container) and merges them into a single root <svg> element, preserving their visual stacking order.
- Uses getBBox() on the chart SVG to measure only the rendered content height, so hidden sample layers do not produce excess whitespace above the gene call panel.
- Places the gene call panel (normally fixed at the bottom of the viewport) immediately below the chart content in the exported layout.
- Adds the split name as a title at the top of the figure, matching the style of the inspect page header (page_header bold + " detailed").
- Injects a minimal inline <style> block with the axis CSS rules from charts.css (fill: none; stroke: #aaa) so axis lines render at the correct weight and colour without a live stylesheet.
- Strips the brush/slider element (g.brush) from the gene call panel, since it is purely interactive and would otherwise render as a solid black box in a static file.
- Downloads the result as a well-formed SVG file (with XML declaration and DOCTYPE) named after the split.

I am not a JavaScript-savvy person, but I asked Claude to match the existing export code for the main interactive page whenever possible, and I did read through the code to ensure it looks reasonable. I've tested the export with and without hidden sample layers, with and without SNVs being shown, and the resulting SVGs look good. One example:

<img width="1467" height="1476" alt="TARA_SAMEA4398168_MAG_00000025_000000000042_split_00001" src="https://github.com/user-attachments/assets/8804f5fe-a67b-4d63-8ddc-53e6b81f4b12" />

Still, I'd appreciate if someone else would test this as well before we merge :) Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd3f96769f41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.