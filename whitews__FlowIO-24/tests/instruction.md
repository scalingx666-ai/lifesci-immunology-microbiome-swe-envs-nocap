# Issue

**Title:** Bugfix: Integer values aren't read according to FCS standard.

## Description

Hey,
While working with some `lmd` files with integer values, most of the data wasn't right (compared it with `flowCore`). Researching the [FSC standard](https://www.genepattern.org/attachments/fcs_3_1_standard.pdf) the reason is that even if the `PnB` value describes a bitwidth for each value, the `PnR` value specifies how many bits are really used for the measurement, while the remaining bits don't have any meaning. If they where all 0 it wouldn't be problem, but the manufactures seem to write something in there, which causes far to big values. I tried to fix it according to the standard by creating a bit mask and applying it to the raw bytes. 

PS: One of the test files seemed a bit awkward cause it had integer values, but the range param wasn't a power of two, I just changed the expected value to check if the tests can succeed. But maybe you know more about this file, @whitews ?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad1ad74aaec1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.