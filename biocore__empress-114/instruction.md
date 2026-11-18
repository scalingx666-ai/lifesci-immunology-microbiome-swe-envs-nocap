# Issue

**Title:** Set up headless testing with qunit-puppeteer

## Description

This should make headless testing on travis work, although this solution does have some inherent shortcomings . This should at least get us up and running with Travis right now.

Other things worth noting:
- The travis YAML file is just a shortened version of the file @kwcantrell added in #111. ~~I don't think we need to be bound to Node.js 10 or anything -- I just wanted to be consistent :)~~
- As mentioned in #111, it would be good to eventually keep track of code coverage. I know Karma can do this (see e.g. [here](https://ariya.io/2013/10/code-coverage-of-qunit-tests-using-istanbul-and-karma)), and I'm sure there are ways to do this through Puppeteer (but I don't think a way currently exists for doing this through qunit-puppeteer in particular). There are lots of conceivable ways to get this done; I can try to work on that next if you'd like.

Thanks! @ElDeveloper / anyone else, let me know if you'd like me to change anything.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `69fb599d0079`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.