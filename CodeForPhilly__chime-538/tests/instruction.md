# Issue

**Title:** Refactor deployment workflows based on GitHub Releases

## Description

This change set heavily refactors the automated deployment workflow to circumvent challenges with using GitHub actions for CD and to more closely match the current development release process. The workflow implemented is as follows:

* When a [GitHub release is created](https://help.github.com/en/github/administering-a-repository/managing-releases-in-a-repository#creating-a-release), build a container image from the release and publish the image to GitHub packages
  * The main implication here is that we are performing builds when a release is created, rather than when a new tag is pushed
* After image is published, edit the k8s/app.yaml manifest to deploy the new image version, add the manifest to a zip file, and publish the zip file to the Release
  * For prod releases, the app.yaml manifest will be packaged with the manifests in k8s.prod
  * For pre-releases, the app.yaml manifest will be packaged with the manifests in k8s.preprod
* Next step is dependent on wether the release is marked as a pre-release or a full release:
  * For pre-releases, download the manifest files published in step 2 and apply them to the preprod cluster
  * For full releases, download the manifeast files published in step 2, acquire a diff via `kubectl diff`, and open a PR from develop into releases/v1 containing the diff in the description
* FULL RELEASES ONLY: Once the PR is merged, download the manifest files which were published to the Release and apply them to the production cluster

This workflow will allow the development team to perform releases without any intervention from the ops unit. Working examples of workflow steps:

- [Published pre-release](https://github.com/lottspot/chime/releases/tag/v0.0.2-rc.1)
- [Pre-release workflow run](https://github.com/lottspot/chime/actions/runs/75570366)
- [Published full release](https://github.com/lottspot/chime/releases/tag/v0.0.2)
- [Full release workflow run](https://github.com/lottspot/chime/actions/runs/75578572)
- 
- [Deploy workflow from PR merge](https://github.com/lottspot/chime/actions/runs/75585024)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46a532fc2a81`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.