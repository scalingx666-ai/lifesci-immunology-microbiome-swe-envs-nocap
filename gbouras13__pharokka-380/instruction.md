# Issue

**Title:** logger has no attribute exit

## Description

I supplied an incorrect custom hmm (one with the suffix `.hmm`) 

And got this error message:
```
Traceback (most recent call last):
  File "/usr/local/bin/pharokka.py", line 489, in <module>
    main()
  File "/usr/local/bin/pharokka.py", line 116, in main
    validate_custom_hmm(args.custom_hmm)
  File "/usr/local/bin/input_commands.py", line 640, in validate_custom_hmm
    logger.exit(
AttributeError: 'Logger' object has no attribute 'exit'
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29bcf33016cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.