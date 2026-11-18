# Issue

**Title:** Tornado fetch file from central handler

## Description

This the accompanying PR to 

**In short:** I've extended fetch and push from only files to also directories. ~~In test mode, objects can also be deleted.~~ Depending on the route of API calls (through nginx =  8383 OR directly to tornado = 2117x), file delivery is handled differently to make us of nginx's much faster transfer capability

**More elaborate**:
1. Resetting the DB of qiita is done by triggering the `/apitest/reset/` endpoint (and also others). However, this only works properly if qiita master is addressed. Tests therefore do **not** speak against nginx (port 8383) but directly with the master instance (port 21174). However, when sending files, I relied on delivery through nginx. If requests go directly to master, the file content will be empty - and tests fail. With PR  the according endpoint checks if a request was made through nginx (and then uses it's fast mechanism to deliver the file) or directly to the tornado instance (which now can also send the file in a much slower fashion). Should be fast enough for testing.
2. Similarly, clients can now fetch directories. As I fear that misbehaving clients might trigger fetching the whole QIITA_BASE_DIR, I am limiting this to those directories that are "managed" by Qiita's DB as filetype directory.
3. ~~I realized that https://github.com/qiita-spots/qtp-sequencing/blob/4a325e7a75ca989eea9d9029acd02be2384a601e/qtp_sequencing/validate.py#L81 is directly deleting files in QIITA_BASE_DIR. Therefore, I added an according function to qiita_client and qiita, but only delete the file when using "filesystem" protocol OR qiita is run in test mode as I am too skeptical about providing an API endpoint to delete arbitrary files.~~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e0e7480a1b04`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.