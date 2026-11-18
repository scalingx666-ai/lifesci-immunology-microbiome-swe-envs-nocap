# Issue

**Title:** add trailing/separating whitespace

## Description

got the error `Error running SQL: SYNTAX_ERROR. MSG: trailing junk after numeric literal at or near "1A" LINE 6: WHERE study_id = 1AND artifact_type = '... ^ ` on my test instance

log says
```
==> bcf_qiita/Logs/qiita_21174.log <==
[E 240322 13:35:00 web:1669] Uncaught exception GET /study/description/1 (127.0.0.1)
    HTTPServerRequest(protocol='https', host='qiita.jlab.bio', method='GET', uri='/study/description/1', version='HTTP/1.0', remote_ip='127.0.0.1')
    Traceback (most recent call last):
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 256, in _execute
        cur.execute(sql, sql_args)
      File "/homes/sjanssen/bcf_qiita/envs/qiita/lib/python3.9/site-packages/psycopg2/extras.py", line 146, in execute
        return super().execute(query, vars)
    psycopg2.errors.SyntaxError: trailing junk after numeric literal at or near "1A"
    LINE 6:                      WHERE study_id = 1AND artifact_type = '...
                                                  ^
    
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 199, in _raise_execution_error
        raise ValueError(
    ValueError: Error running SQL: SYNTAX_ERROR. MSG: trailing junk after numeric literal at or near "1A"
    LINE 6:                      WHERE study_id = 1AND artifact_type = '...
                                                  ^
    
    
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/homes/sjanssen/bcf_qiita/envs/qiita/lib/python3.9/site-packages/tornado/web.py", line 1590, in _execute
        result = method(*self.path_args, **self.path_kwargs)
      File "/homes/sjanssen/bcf_qiita/envs/qiita/lib/python3.9/site-packages/tornado/web.py", line 3006, in wrapper
        return method(self, *args, **kwargs)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_pet/handlers/study_handlers/base.py", line 28, in get
        study_info = study_get_req(study, self.current_user.id)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_pet/handlers/api_proxy/studies.py", line 120, in study_get_req
        study.artifacts(artifact_type='BIOM')) != 0
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/study.py", line 1108, in artifacts
        for aid in qdb.sql_connection.TRN.execute_fetchflatten()]
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 49, in wrapper
        return func(self, *args, **kwargs)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 389, in execute_fetchflatten
        return list(chain.from_iterable(self.execute()[idx]))
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 49, in wrapper
        return func(self, *args, **kwargs)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 313, in execute
        return self._execute()
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 260, in _execute
        self._raise_execution_error(sql, sql_args, e)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 205, in _raise_execution_error
        raise ValueError("Error running SQL query: %s" % str(error))
    ValueError: Error running SQL query: Error running SQL: SYNTAX_ERROR. MSG: trailing junk after numeric literal at or near "1A"
    LINE 6:                      WHERE study_id = 1AND artifact_type = '...
                                                  ^
    
    
[E 240322 13:35:00 web:2161] 500 GET /study/description/1 (127.0.0.1) 159.63ms
[E 240322 13:35:00 web:1114] Uncaught exception in write_error
    Traceback (most recent call last):
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 256, in _execute
        cur.execute(sql, sql_args)
      File "/homes/sjanssen/bcf_qiita/envs/qiita/lib/python3.9/site-packages/psycopg2/extras.py", line 146, in execute
        return super().execute(query, vars)
    psycopg2.errors.SyntaxError: trailing junk after numeric literal at or near "1A"
    LINE 6:                      WHERE study_id = 1AND artifact_type = '...
                                                  ^
    
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 199, in _raise_execution_error
        raise ValueError(
    ValueError: Error running SQL: SYNTAX_ERROR. MSG: trailing junk after numeric literal at or near "1A"
    LINE 6:                      WHERE study_id = 1AND artifact_type = '...
                                                  ^
    
    
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/homes/sjanssen/bcf_qiita/envs/qiita/lib/python3.9/site-packages/tornado/web.py", line 1590, in _execute
        result = method(*self.path_args, **self.path_kwargs)
      File "/homes/sjanssen/bcf_qiita/envs/qiita/lib/python3.9/site-packages/tornado/web.py", line 3006, in wrapper
        return method(self, *args, **kwargs)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_pet/handlers/study_handlers/base.py", line 28, in get
        study_info = study_get_req(study, self.current_user.id)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_pet/handlers/api_proxy/studies.py", line 120, in study_get_req
        study.artifacts(artifact_type='BIOM')) != 0
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/study.py", line 1108, in artifacts
        for aid in qdb.sql_connection.TRN.execute_fetchflatten()]
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 49, in wrapper
        return func(self, *args, **kwargs)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 389, in execute_fetchflatten
        return list(chain.from_iterable(self.execute()[idx]))
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 49, in wrapper
        return func(self, *args, **kwargs)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 313, in execute
        return self._execute()
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 260, in _execute
        self._raise_execution_error(sql, sql_args, e)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 205, in _raise_execution_error
        raise ValueError("Error running SQL query: %s" % str(error))
    ValueError: Error running SQL query: Error running SQL: SYNTAX_ERROR. MSG: trailing junk after numeric literal at or near "1A"
    LINE 6:                      WHERE study_id = 1AND artifact_type = '...
                                                  ^
    
    
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 256, in _execute
        cur.execute(sql, sql_args)
      File "/homes/sjanssen/bcf_qiita/envs/qiita/lib/python3.9/site-packages/psycopg2/extras.py", line 146, in execute
        return super().execute(query, vars)
    psycopg2.errors.UniqueViolation: duplicate key value violates unique constraint "pk_logging"
    DETAIL:  Key (logging_id)=(294) already exists.
    
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 199, in _raise_execution_error
        raise ValueError(
    ValueError: Error running SQL: UNIQUE_VIOLATION. MSG: duplicate key value violates unique constraint "pk_logging"
    DETAIL:  Key (logging_id)=(294) already exists.
    
    
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/homes/sjanssen/bcf_qiita/envs/qiita/lib/python3.9/site-packages/tornado/web.py", line 1112, in send_error
        self.write_error(status_code, **kwargs)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_pet/handlers/base_handlers.py", line 69, in write_error
        LogEntry.create(
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/logger.py", line 103, in create
        return cls(qdb.sql_connection.TRN.execute_fetchlast())
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 49, in wrapper
        return func(self, *args, **kwargs)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 336, in execute_fetchlast
        return self.execute()[-1][0][0]
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 49, in wrapper
        return func(self, *args, **kwargs)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 313, in execute
        return self._execute()
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 260, in _execute
        self._raise_execution_error(sql, sql_args, e)
      File "/homes/sjanssen/bcf_qiita/qiita-spots/qiita/qiita_db/sql_connection.py", line 205, in _raise_execution_error
        raise ValueError("Error running SQL query: %s" % str(error))
    ValueError: Error running SQL query: Error running SQL: UNIQUE_VIOLATION. MSG: duplicate key value violates unique constraint "pk_logging"
    DETAIL:  Key (logging_id)=(294) already exists.
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d743a810202a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.