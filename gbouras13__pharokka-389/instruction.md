# Issue

**Title:** Fixed issue with phanotate.py displaying warning message

## Description

When running pharokka, I had received the following error...

```
Traceback (most recent call last):
  File "/projects/rrc_shared/common/conda_envs/pharokka-1.7.5/bin/pharokka.py", line 489, in <module>
    main()
  File "/projects/rrc_shared/common/conda_envs/pharokka-1.7.5/bin/pharokka.py", line 128, in main
    ) = check_dependencies(args.skip_mash)
  File "/mmfs1/projects/rrc_shared/common/conda_envs/pharokka-1.7.5/bin/input_commands.py", line 386, in check_dependencies
    phanotate_major_version = int(phanotate_version.split(".")[0])
ValueError: invalid literal for int() with base 10: '/projects/rrc_shared/common/conda_envs/pharokka-1'
```

Root cause was that phanotate.py is printing an warning message due to the fact that pkg_resources is deprecated

```
$ phanotate.py --version
/projects/rrc_shared/common/conda_envs/pharokka-1.7.5/lib/python3.10/site-packages/phanotate_modules/file_handling.py:13: UserWarning: pkg_resources is deprecated as an API
. See https://setuptools.pypa.io/en/latest/pkg_resources.html. The pkg_resources package is slated for removal as early as 2025-11-30. Refrain from using this package or pi
n to Setuptools<81.
  import pkg_resources
1.5.1
```

The update has the Popen object in pharokka redirect STDERR to the null device to ignore the warning message when trying to parse the version number for phanotate.py

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0189bd174269`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.