# Issue

**Title:** Survey updates

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

Make survey scales more consistent, add gastrointestinal issues and headache to symptoms questions, make Q3 a scale. Updated behavior scales. Attempted to align the survey more with the [data model](https://docs.google.com/spreadsheets/d/1gifZGnj-ntIOXbZrRY4S5KEULoV64DCbi0pZSVWKsns/edit#gid=0).

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

<!-- Make sure tests pass on both Travis and Circle CI. -->

**Everything**

![the-whole-thang](https://user-images.githubusercontent.com/16993949/79532591-989fe000-8043-11ea-95ec-8c51efd3ed84.gif)

**Page 1**

![page-1](https://user-images.githubusercontent.com/16993949/79532593-9c336700-8043-11ea-8a31-c26c52c18a20.png)

**Page 2**

![page-2](https://user-images.githubusercontent.com/16993949/79532740-00eec180-8044-11ea-82cb-c269f78bf0e2.gif)

**Page 3**

![page-3](https://user-images.githubusercontent.com/16993949/79532616-a6556580-8043-11ea-8223-dc944b95e447.png)

**Page 4**

![page-4](https://user-images.githubusercontent.com/16993949/79532747-04824880-8044-11ea-8c78-850a8a3419bf.gif)

**Show Me More**

![show-me-more](https://user-images.githubusercontent.com/16993949/79532636-af463700-8043-11ea-9992-9dae223f5d53.png)

### Final Checklist

- [x] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [x] Have you added any new tests necessary?
- [x] Is your PR rebased off the most current master?
- [x] Have you squashed all commits, or if you will merge will you squash all commits?
- [x] Did you use yarn, not npm?
- [x] Did you use Material-UI wherever possible?
- [x] Did you format according to Prettier?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74675c021ad6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.