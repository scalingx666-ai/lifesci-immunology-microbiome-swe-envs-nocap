# Issue

**Title:** Structure display overhaul

## Description

Before:
<img width="1220" height="885" alt="image" src="https://github.com/user-attachments/assets/2e17d589-d461-4d49-9fa9-e8c5936e7251" />
After:
<img width="1220" height="885" alt="image" src="https://github.com/user-attachments/assets/adeabf10-5562-4b7c-ad10-e88df47860d3" />

Front end is not my expertise at all, so all changes are the work of Claude under my supervision.

# What changes
Bring back the language of the classic anvi'o interface, from text font, size and color to color palettes.

Now there is a collapsable setting panel and the prot structure view resize accordingly.
The tabs are the same as before and on the bottom, we have buttons to export the pdb, the pymol code, picture, and the variability data.

The filter tab changed look:
<img width="494" height="460" alt="image" src="https://github.com/user-attachments/assets/5e74e83e-2b33-4e13-bdcb-4a4b5fd6752e" />

Nicer looking sliders and barplot + gray shading for unselected data + manual range section if you want.
And clickable toggle to select amino acids. I like this upgrade a lot.

# What's not included
As mentioned in #2769, I want to include the libraries to display the structure instead of downloading them on the fly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4d791816ea0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.