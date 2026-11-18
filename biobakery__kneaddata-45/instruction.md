# Issue

**Title:** fix: append all split FASTA files to the list for TRF execution

## Description

We welcome feedback and issue reporting for all bioBakery tools through our [Discourse site](https://forum.biobakery.org/c/pull-request/featurepull-request/). For users that would like to directly contribute to the [tools](https://github.com/biobakery/) we are happy to field PRs to address **bug fixes**. Please note the turn around time on our end might be a bit long to field these but that does not mean we don't value the contribution! We currently **don't** accept PRs to add **new functionality** to tools but we would be happy to receive your feedback on [Discourse](https://forum.biobakery.org/c/pull-request/featurepull-request/).

Also, we will make sure to attribute your contribution in our User’s manual(README.md) and in any associated paper Acknowledgements.


## Description
The size of the output FASTQ file is different when the `-t` argument is greater then 1. 
I found that it might be caused by line 124 in kneaddata/trf_parallel.py 
Since `file_handle_write` is always not None after the file is opened(line 124), only the first temporary file is appended to the `tempfile_written_list` and `datfile_to_write_list`(line 115~116). As a result, the trf command actually executes only one parallel temporary file.

## Related Issue
<!--- If fixing a bug, there should be an issue describing it with steps to reproduce -->
<!--- Please link to the issue here: -->


## Screenshots (if appropriate):

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fdc9a6bddd8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.