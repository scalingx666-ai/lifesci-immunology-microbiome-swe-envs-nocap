# Issue

**Title:** Purge non-verified user

## Description

Handle #3416 first!

Addressing #3378 as well.
This PR is based on user creation_timestamp logging and offers a new Admin only page that lists those users that 
a) are non yet verifier (i.e. user_status_id==5) and 
b) where registers more than 30 days ago (give a new user sufficient time to react)
Individual or all users can be selected in the website and removed by one click.

![image](https://github.com/qiita-spots/qiita/assets/11960616/68b7a37f-1d0e-49ee-9ee6-88bc81dd075d)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b3f717ac9d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.