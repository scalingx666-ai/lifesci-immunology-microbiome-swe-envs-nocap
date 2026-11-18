# Issue

**Title:** Errhandling non dict values

## Description

When in test mode, you populate the database with `""` values for `command_parameters` of table `qiita.processing_job` here https://github.com/qiita-spots/qiita/blob/fdad618cc6283430decc6511c0cc6b9b477c1fb6/qiita_db/support_files/patches/test_db_sql/92.sql#L7-L11

Thus, when logged in as `admin@foo.bar`, qiita will raise AttributeErrors like:
```
[E 250307 07:55:30 web:1669] Uncaught exception GET /user/jobs/ (172.27.0.16)
    HTTPServerRequest(protocol='https', host='localhost', method='GET', uri='/user/jobs/', version='HTTP/1.0', remote_ip='172.27.0.16')
    Traceback (most recent call last):
      File "/opt/conda/envs/qiita/lib/python3.9/site-packages/tornado/web.py", line 1590, in _execute
        result = method(*self.path_args, **self.path_kwargs)
      File "/opt/conda/envs/qiita/lib/python3.9/site-packages/tornado/web.py", line 3006, in wrapper
        return method(self, *args, **kwargs)
      File "/qiita/qiita_pet/handlers/user_handlers.py", line 380, in get
        response = user_jobs_get_req(self.current_user)
      File "/qiita/qiita_core/util.py", line 83, in wrapper
        return func(*args, **kwargs)
      File "/qiita/qiita_pet/handlers/api_proxy/user.py", line 40, in user_jobs_get_req
        'params': j.parameters.values,
      File "/qiita/qiita_db/processing_job.py", line 724, in parameters
        return qdb.software.Parameters.load(
      File "/qiita/qiita_db/software.py", line 1637, in load
        parameters.update(missing_in_user)
    AttributeError: 'str' object has no attribute 'update'
```
This problem might not occur in a production environment, but since the `load` function already handles wrong use of parameters, I thought it might complement the current mechanism to also raise a more speaking error in this situation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba134039f4d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.