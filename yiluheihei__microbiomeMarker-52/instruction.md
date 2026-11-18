# Issue

**Title:** improve heatmap visual

## Description

Hi @yiluheihei 

Thanks for the interesting package. I have implemented two more options for heatmap visualization:
`use_gghue`  use ggplot2 palette, which can be consistent with `plot_abundance`, etc. It's a bit hard to control the annotation colors using the default `complexheatmap` palette. 
`scale_by_row` scale the matrix by row, which may be eye-friendly for some weak signals.
These are some personal choices for plots. So you can make a decision if you want to include them. 

```
plot_heatmap(mm_edger, transform = "log10p", group = "Class")
```
![image](https://user-images.githubusercontent.com/30360815/143902796-49b5c88e-d96c-4955-b1b1-5d51b2a88dbc.png)
```
plot_heatmap(mm_edger, transform = "log10p", group = "Class", use_gghue = FALSE )   
```
![image](https://user-images.githubusercontent.com/30360815/143903070-37ec0210-dd0e-4100-9a7c-8225f0eb7032.png)
```
plot_heatmap(mm_edger, transform = "log10p", group = "Class", scale_by_row = TRUE )
```
![image](https://user-images.githubusercontent.com/30360815/143903255-1e6aa887-9b85-4ba6-b098-cee31991dd89.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e624fdcfa08`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.