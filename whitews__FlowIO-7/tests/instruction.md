# Issue

**Title:** Modify __parse_pairs to take into account delimiter == '*'

## Description

Hello again, 

I had an issue trying to open a fcs3.1 file with delimiter "*" in the header text. The issue was located at this step : 
![error2](https://user-images.githubusercontent.com/52413616/108341959-84d08780-71da-11eb-8fc9-071bc611d810.png)

I corrected it adding a condition in the function __parse_pairs of flowdata.py with the following : 
![correction](https://user-images.githubusercontent.com/52413616/108342080-ae89ae80-71da-11eb-9a60-39fa0fe78396.png)

And then I was able to load my fcs file without error. I ran run_tests.py after the modification and it still work.
Louis

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `087878b1faca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.