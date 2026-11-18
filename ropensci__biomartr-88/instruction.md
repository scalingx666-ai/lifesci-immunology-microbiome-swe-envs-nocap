# Issue

**Title:** https and new curl fix

## Description

Hello again, times are changing and https URLs is now starting to be enforced for many systems.

That being the case I fear biomartr will start to fail for many of the calls to older "http" URLs.
I here did a small fix for the most important links for ensemble genomes. 
To keep biomartr alive, hopefully if enough people do some small fixes when needed it can continue to function properly.

Secondly, the newest curl-lib now enforces a trailing slash on URL directories, which made one of your FTP file checkers fail.
I made a safety wrapper for the dir check, that always enforces a single slash end.

The changes I made are completely backwards compatible for others, while making it not crash on people with newer systems.

I tested it on 2 systems, and ran your checks.

I see that your full checks (The ones ignored on CRAN) fails for several points, by giving https links I fixed some of them, but a new commit is needed to fix more of them.
Idealy some of your links should be moved out to a single function, so that if it ever changes in the future, there will be only 1 line to edit instead of a 100 which it is currently. 

Especially this call:
```
jsonlite::fromJSON(
            "http://rest.ensembl.org/info/data/?content-type=application/json"
    )$releases
```
Which I changed to:
```
jsonlite::fromJSON(
            "https://rest.ensembl.org/info/data/?content-type=application/json"
    )$releases
```

It is used over 20 times, and it is far from the only one. So there is a lot of redundancy that could be moved to a single function :)

Merry Christmas :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `89b6fb6dcb5b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.