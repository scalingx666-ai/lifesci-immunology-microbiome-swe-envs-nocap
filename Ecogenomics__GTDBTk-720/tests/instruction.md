# Issue

**Title:** Improve tk

## Description

This pull request introduces several improvements and bug fixes across the codebase, focusing on more robust handling of file symlinks, improved logging for unclassified genomes, performance optimizations, and code simplification. The most important changes are grouped by theme below.

**Robustness and Correctness Improvements:**

* [`gtdbtk/tools.py`](diffhunk://#diff-f6381a9aa31b684abf71606bfa0c98c04e56550b0f457f7a6d1e7d3d3fcca118L248-R255): Improved the `symlink_f` function to correctly remove existing files or dangling symlinks at the destination before creating a new symlink, preventing errors when re-running with moved input files.
* [`gtdbtk/split.py`](diffhunk://#diff-6c3dc0b022bb742f9bd6e42fe0cc4b99b1831af2948d69955194d509ea7fd2cdL244-R246): Fixed error handling in `_classify_on_internal_branch` by providing a more informative error message and correcting the logic for finding the closest rank, avoiding hidden exceptions. [[1]](diffhunk://#diff-6c3dc0b022bb742f9bd6e42fe0cc4b99b1831af2948d69955194d509ea7fd2cdL244-R246) [[2]](diffhunk://#diff-6c3dc0b022bb742f9bd6e42fe0cc4b99b1831af2948d69955194d509ea7fd2cdL285-R284)

**Logging and User Feedback:**

* [`gtdbtk/classify.py`](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dL487-R489): Centralized and improved the logging of unclassified genomes due to Prodigal or alignment failures by introducing the `_log_unclassified_failed_genomes` method, ensuring consistent and clear warnings. [[1]](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dL487-R489) [[2]](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dL757-R755) [[3]](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dR1434-R1469)

**Performance and Efficiency:**

* [`gtdbtk/classify.py`](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dR1434-R1469): Optimized taxonomy lookups in the `formatnote` method by introducing the `canonical_taxonomy` property, avoiding repeated re-keying of large taxonomy dictionaries on every call. All relevant calls now use this cached property. [[1]](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dR1434-R1469) [[2]](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dL1494-R1511) [[3]](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dL1851-R1868) [[4]](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dL1860-R1877)

**Code Simplification and Consistency:**

* `gtdbtk/files/marker/tophit.py` and `gtdbtk/files/marker/copy_number.py`: Simplified and standardized how the most significant hit is determined by using `max()` with the `@functools.total_ordering` decorator for the `Hit` class, removing unnecessary custom sorting and the unused `__gt__` method. [[1]](diffhunk://#diff-8e8a052df28db7fdea08daf4ad6c109d09bc8ff092a8eff631dc237056d5a7e3R18) [[2]](diffhunk://#diff-8e8a052df28db7fdea08daf4ad6c109d09bc8ff092a8eff631dc237056d5a7e3R27) [[3]](diffhunk://#diff-8e8a052df28db7fdea08daf4ad6c109d09bc8ff092a8eff631dc237056d5a7e3L63-L77) [[4]](diffhunk://#diff-8e8a052df28db7fdea08daf4ad6c109d09bc8ff092a8eff631dc237056d5a7e3L120-R107) [[5]](diffhunk://#diff-07fdddc6d302ecfa333aa35b12eb969cfb65a02cac000061467a5ce5794ccf6fL76-R76)

**Bug Fixes:**

* [`gtdbtk/classify.py`](diffhunk://#diff-a4ecce2b2cb1d438d86f95635e44aa48dfca4de227c3d5c64df4e510d334c54dL326-R333): Ensured that the ANI screening step is correctly skipped when the `--genes` flag is set, preventing inappropriate execution of nucleotide-based comparisons on protein inputs.

These changes collectively enhance reliability, performance, and maintainability of the codebase.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a93617ae4bcf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.