# Issue

**Title:** Enh/history

## Description

Execution flow rewrite (`dags/covid_etl_dag.py`):
replaced tasks executing `qa_checks` function in DAG -> now task executing new `execute_script` function.

with the rewrite, the execution steps are modified by running SQL scripts located in the `snowflake/sql` directory (by creating separate tasks for each script and executing them in parallel. Additional todo: enhance solution by introducing job-ordering).  The SQL scripts can use Jinja (templating lang for python). To use dynamic variables use `snowflake/sql/template_params.json`, where you can define key-value pairs. Key: the variable name, value: value contained by the variable 

added files and directory:
- added `snowflake/sql` directory
- added `snowflake/sql/template_params.json` file

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f74347cd560`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.