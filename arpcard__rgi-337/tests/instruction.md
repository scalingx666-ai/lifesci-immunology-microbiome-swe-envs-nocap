# Issue

**Title:** Added argument to include loose hits in the heatmap

## Description

Loose hits are now possibly included in the heatmap using the argument `--include_loose`. Their color is purple and black  now represents no hit.

```
./rgi heatmap -i tests/outputs/NC_020818.1.json -o tests/outputs/heatmap_test_to_remove
./rgi heatmap -i tests/outputs/ -o tests/outputs/heatmap_test_to_remove_loose_hits --include_loose
./rgi heatmap -i tests/outputs/ -o tests/outputs/heatmap_test_to_remove
```
Produces:
<img width="341" height="521" alt="heatmap_test_to_remove-1" src="https://github.com/user-attachments/assets/52e67f68-4e2e-4a02-8874-2f47b91dc89c" />
<img width="1037" height="3139" alt="heatmap_test_to_remove_loose_hits-1" src="https://github.com/user-attachments/assets/79482a09-e0ba-466b-a2d5-7a26d86bdf8f" />
This might be useful for exploration purpose (e.g. environment that is not well characterized). This was not vibe coded.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8a3f3699537`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.