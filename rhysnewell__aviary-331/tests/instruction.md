# Issue

**Title:** Aviary polish fix

## Description

The original issue was short-read racon polishing failed with `racon error: empty sequence set!` then memory retries occurred but nothing about memory was the issue. What supports this is the 73 patterns loaded from file but the file was empty. 
In the original code after mapping, polish.py pulls the mapped reads back out with seqkit using the regrex `^(\S+?)(?:/[12])?\s?$`. Due to it ending in \s?$ a header only matched if it was a single word. Real headers have a second field after a space `(SRA @ERR.....)` so nothing matched, therefore zero reads extracted. No test ever simulated/tested for this. 
Now the code is `^(\S+?)(?:/[12])?(?:\s|$)`, seqkit now takes the read name from the first word and ignores any description, so it still strips /1 or /2 straight after the name. And now all mapped read are found again.

Two regression test were additional created. 
- Firstly, this code change was reverted and ran a normal run and error occurred, with this fix the run finishes successfully. 
- A Test that has a SRA-styled header with a description, checking whether the stripping and matching occur correctly. 
- A single word header, checking whether the read is still found so existing methodology isn't broken. 

---

Additionally fixed the Documentation Page not Deploying properly

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba54e0dc0c41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.