# Issue

**Title:** refactor PushFileToCentralHandler to transfer ONE file, but chunked

## Description

I had to realize that pushing larger (>2 GB) files from client to Qiita main exceeds some limited. Therefore, we need to transfer files in a chunked fashion, similar to file upload to Qiita. 

This PR refactors PushFileToCentralHandler::push such that it transfers a single chunk of a single file. The consumer needs to define the chunk number and total expected chunks, too.

Error was
```
>>> qclient.push_file_to_central("/ERR16697941_2.fastq.gz")
2026-03-25 08:19:18,607 qiita_client.qiita_client DEBUG    Submitting file /ERR16697941_2.fastq.gz to qiita server via https
2026-03-25 08:19:18,608 qiita_client.qiita_client DEBUG    Entered QiitaClient.post(/cloud/push_file_to_central/)
2026-03-25 08:19:18,608 qiita_client.qiita_client DEBUG    Entered QiitaClient._request_retry()
2026-03-25 08:19:18,608 qiita_client.qiita_client DEBUG    Entered QiitaClient._request_oauth2()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.9/site-packages/qiita_client/qiita_client.py", line 978, in push_file_to_central
    self.post(
  File "/usr/local/lib/python3.9/site-packages/qiita_client/qiita_client.py", line 524, in post
    return self._request_retry(
  File "/usr/local/lib/python3.9/site-packages/qiita_client/qiita_client.py", line 384, in _request_retry
    r = self._request_oauth2(
  File "/usr/local/lib/python3.9/site-packages/qiita_client/qiita_client.py", line 304, in _request_oauth2
    r = req(*args, **kwargs)
  File "/usr/local/lib/python3.9/site-packages/requests/sessions.py", line 637, in post
    return self.request("POST", url, data=data, json=json, **kwargs)
  File "/usr/local/lib/python3.9/site-packages/requests/sessions.py", line 589, in request
    resp = self.send(prep, **send_kwargs)
  File "/usr/local/lib/python3.9/site-packages/requests/sessions.py", line 703, in send
    r = adapter.send(request, **kwargs)
  File "/usr/local/lib/python3.9/site-packages/requests/adapters.py", line 644, in send
    resp = conn.urlopen(
  File "/usr/local/lib/python3.9/site-packages/urllib3/connectionpool.py", line 787, in urlopen
    response = self._make_request(
  File "/usr/local/lib/python3.9/site-packages/urllib3/connectionpool.py", line 493, in _make_request
    conn.request(
  File "/usr/local/lib/python3.9/site-packages/urllib3/connection.py", line 514, in request
    self.send(chunk)
  File "/usr/local/lib/python3.9/http/client.py", line 1001, in send
    self.sock.sendall(data)
  File "/usr/local/lib/python3.9/ssl.py", line 1240, in sendall
    v = self.send(byte_view[count:])
  File "/usr/local/lib/python3.9/ssl.py", line 1209, in send
    return self._sslobj.write(data)
OverflowError: string longer than 2147483647 bytes
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2e182bca798`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.