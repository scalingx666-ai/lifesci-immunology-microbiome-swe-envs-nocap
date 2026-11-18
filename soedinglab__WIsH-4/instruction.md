# Issue

**Title:** added Docker file

## Description

building the image:

```
cd /path/to/repository/of/WiSH
docker build -t wish .
```

printing the help: `docker run wish`
mounting data in the container: `docker run -v /some/host/folder:/data wish <some WiSH commands>`

`/data` is the working directory inside the docker container

🐳

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e1a4b914ff0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.