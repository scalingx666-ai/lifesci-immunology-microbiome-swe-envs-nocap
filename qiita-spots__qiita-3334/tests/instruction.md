# Issue

**Title:** sync max body size

## Description

I am not totally sure if my analysis is accurate. Here is my understanding of the problem.

While setting up a qiita instance, we stumbled upon issues when uploaded files. File < chunk size were not affected. Also, this error only occurred when qiita run within the nginx setup, not as pure python instance. It looks like there is a default maximum body size for GET commands of [1M](http://nginx.org/en/docs/http/ngx_http_core_module.html#client_max_body_size) in nginx. Therefore, you might want to increase this size in the `nginx_example.conf` or at least leave a comment to inform others.
I have not tested to set this value to `3M`, but I recognized that the actual size of the payload various around 3400000 byte, thus some buffer could be useful.

Ideally, both values would be sources from a configure file instead of "hard coding" them into the javascript and the nginx config file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c1a4a7112c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.