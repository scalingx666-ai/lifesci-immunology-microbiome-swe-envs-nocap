# Issue

**Title:** independent run of semibin

## Description

@SilasK  I have accomplished a test run of `semibin`, but rely on existence of `Cobinning/filtered_contigs/{sample}.fasta`. Small bug fix:

1.         " --minfasta-kbs {params.min_bin_kbs}"
it seems to only accept integer type. I am not sure if you met this.

2.         fasta=ancient("Cobinning/filtered_contigs/{sample}.fasta"),
The `ancient` flag in `semibin.smk` seems to be in conflict in the `temp` flag in `cobinning.smk`
I couldn't run `semibin` independently if I didn't keep the `filtered_contig` output from `cobinning.smk`.
I tried it in new working directory, directly run `atlas run None semibin --profile cluster`. It works fine if specifying `--dry-run`. But it fails in a real run.
```
Traceback (most recent call last):
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/__init__.py", line 699, in snakemake
    success = workflow.execute(
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/workflow.py", line 1056, in execute
    success = scheduler.schedule()
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/scheduler.py", line 477, in schedule
    run = self.job_selector(needrun)
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/scheduler.py", line 816, in job_selector_greedy
    c = list(map(self.job_reward, jobs))  # job rewards
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/scheduler.py", line 898, in job_reward
    temp_size = self.dag.temp_size(job)
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/dag.py", line 597, in temp_size
    return sum(f.size for f in self.temp_input(job))
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/dag.py", line 597, in <genexpr>
    return sum(f.size for f in self.temp_input(job))
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/io.py", line 251, in wrapper
    return func(self, *args, **kwargs)
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/io.py", line 266, in wrapper
    return func(self, *args, **kwargs)
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/io.py", line 569, in size
    return self.size_local
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/io.py", line 574, in size_local
    self.check_broken_symlink()
  File "/home/projects/cu_10168/people/yanhui/bin/miniconda3/envs/atlas-dev/lib/python3.8/site-packages/snakemak
e/io.py", line 579, in check_broken_symlink
    if not self.exists_local and os.lstat(self.file):
FileNotFoundError: [Errno 2] No such file or directory: 'Cobinning/filtered_contigs/sample1.fasta'
```
It's wired... but probably related with 
I kept the `temp` flag for `filtered_contigs` output in `semibin.smk`. And it works.
It shall/may not change your phylosiphy of avoiding recreation of files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ecb376c3f27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.