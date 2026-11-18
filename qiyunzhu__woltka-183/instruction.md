# Issue

**Title:** BUG: Ignore hidden files when reading directory

## Description

These are some proposed changes to avoid trying to parse hidden files. I ran into this issue in macOS when inputing a directory where a hidden file `.DS_Store` file had been created by the OS.

```
Input directory: sams/.
Number of alignment files to read: 11.
Demultiplexing: off.
Constructing classification system...
  Parsing Newick tree file: tree.nwk... Done.
Classification system constructed.
  Total number of classification units: 20603.
Classification will operate on these ranks: free.
Parsing alignment file .DS_Store Traceback (most recent call last):
  File "/Users/yoshiki/miniconda3/envs/mg/bin/woltka", line 8, in <module>
    sys.exit(cli())
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/click/core.py", line 1128, in __call__
    return self.main(*args, **kwargs)
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/click/core.py", line 1053, in main
    rv = self.invoke(ctx)
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/click/core.py", line 1659, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/click/core.py", line 1395, in invoke
    return ctx.invoke(self.callback, **ctx.params)
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/click/core.py", line 754, in invoke
    return __callback(*args, **kwargs)
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/woltka/cli.py", line 188, in classify_cmd
    workflow(**kwargs)
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/woltka/workflow.py", line 137, in workflow
    zippers, outcov_dir)
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/woltka/workflow.py", line 293, in classify
    for qryque, subque in mapper(fh, fmt=fmt, n=chunk):
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/woltka/align.py", line 58, in plain_mapper
    fmt, head = (fmt, []) if fmt else infer_align_format(fh)
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/site-packages/woltka/align.py", line 204, in infer_align_format
    line = next(fh)
  File "/Users/yoshiki/miniconda3/envs/mg/lib/python3.6/codecs.py", line 321, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x80 in position 3131: invalid start byte
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd36ef73bda1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.