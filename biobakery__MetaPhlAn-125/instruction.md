# Issue

**Title:** Resolve hanging process by replacing sys.exit in thread with raise

## Description

Hello Francesco,

I was running strainphlan on the CRC data sets recently and noticed it ran into an error and then hung. I looked into the code a bit and if you just replace the sys.exit / error function in the thread pool parallel_execution function with raise the code will terminate as expected. The issue with strainphlan hanging after an error is if we run strainphlan in the biobakery workflows (exp in the cloud) and it hangs with an error the workflow thinks the task is still running because it has not terminated. I had this happen with the CRC data and I thought that strainphlan was just taking a very long time until I looked into a bit and realized it had hung. 

Here is a very small pull request. Sorry it might not be worth a pull because it was so small. I had originally started to work on the change and thought it would be a bit more modifications but kept on working on it and got it down to a tiny change. Please check it out and let me know if it will work for you. The error use case that I had run into before that hung will now terminate and print out the following (which I think includes all the info you want to log to stderr).

```
Mon Aug 24 18:57:31 2020: Start StrainPhlAn 3.0 execution
Mon Aug 24 18:57:31 2020: Creating temporary directory...
Mon Aug 24 18:57:31 2020: Done.
Mon Aug 24 18:57:31 2020: Getting markers from main sample files...
[e] Parallel execution fails: string indices must be integers
Mon Aug 24 18:57:31 2020: Stop StrainPhlAn 3.0 execution.
```

Please let me know if you have any questions for me! I am happy to chat on slack if useful.

Thank you!
Lauren

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `446ee61b05a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.