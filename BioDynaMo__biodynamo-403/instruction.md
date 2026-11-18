# Issue

**Title:** Deprecate CentOS 7

## Description

This pull request removes support for CentOS 7 from the project in a minimal invasive way. The most important changes are summarized below:

### Removal of CentOS 7 CI Workflows:
* [`.github/workflows/centos-ci.yml`](diffhunk://#diff-c4a7e7c2e3a8b4517e8c276dd009accfd652e18ef20c998981dcb2b330bf27c8L1-L108): Removed the entire CI workflow for CentOS 7.
* [`.github/workflows/centos-system-ci.yml`](diffhunk://#diff-d7b84745843b6a19639db09d7f658175454a16159ae2948970a58780755322b5L1-L164): Removed the entire system CI workflow for CentOS 7.

### Documentation Updates:
* [`README.md`](diffhunk://#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5L24): Removed the CentOS system CI badge.
* [`doc/dev_guide/build.md`](diffhunk://#diff-80e494c4f29f4980fd427022bf43cb50a0c70abb083ad5c240c0c0ab3c5c0b5bL89-R89): Marked CentOS 7 as deprecated.
* [`doc/user_guide/installation.md`](diffhunk://#diff-4e26aaf8e8de6329b4e6bcc2ecc3e98b6809db0bb7776ff068d84e957dd5de00L63): Removed CentOS 7 from the list of supported platforms.
* [`doc/user_guide/prerequisites.md`](diffhunk://#diff-23cf1a2440b4aac200324ac02307e8e625a6be3f7222975cee43f63d7108fb19L120-R120): Marked CentOS 7 as deprecated and no longer officially supported.

### Legacy Code Notices:
* [`cmake/CheckCompiler.cmake`](diffhunk://#diff-f828ebface69cbdcf498fa505af4c6a1aa12b0c4ce77aea9a30bafaabcdf7da1R25): Added remarks indicating that CentOS 7 is no longer supported.
* [`cmake/env/thisbdm.fish`](diffhunk://#diff-8c2c2370ef601725997450f33bcfff0fa60dc66448815e0829adb8699b2573d6L424-R424): Updated comments to reflect that CentOS specifics are no longer officially supported.
* [`cmake/env/thisbdm.sh`](diffhunk://#diff-e1d4383f3645208b0b23c1c64f010c4c5a8c973890cee18bea55da2aff5775b0L551-R551): Updated comments to reflect that CentOS specifics are no longer officially supported.
* [`test/system/multi_simulation.sh`](diffhunk://#diff-c9f74ae4c3000ac39b827953a37186fc0b3e40c4c944af0031235fa9b605248fR35): Added a notice that CentOS is no longer supported but kept for reference.
* [`util/installation/centos-7/prerequisites.sh`](diffhunk://#diff-6b3ce3f5792ec8a5c641c2dde3bf0823559e381d4ca826acbed646a712002badR16-R19): Added a notice that CentOS is not supported anymore and the script is kept for reference.
* [`util/installation/common/install.sh`](diffhunk://#diff-30deb91b68cce0d30b1c8d8cb0018b5eabee31ed81ad406db94aafc652422870L37-R37): Updated the comment to indicate that custom instructions for CentOS are deprecated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2619fe542c5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.