# Issue

**Title:** Fix heroku deploy

## Description

This PR fixes the broken heroku build. To test it you will need a heroku account and you will need to run 
```bash
heroku stack:set container -a <appname>
heroku git:remote -a <appname>
git push heroku fix_heroku_deploy:master
```

This will set heroku to use docker and will deploy it to your heroku account.

For demonstration purposes this branch has been deployed to https://pennchime.herokuapp.com/

---

## <center>Pull Request Checklist</center>

### <center>For Reviewer</center>

- [x] Submitted under the correct tag
- [x] Runs without error or warning
- [x] Documentation  revised / included
- [ ] Unit tests included
- [ ] Issues referenced
- [x] Does not create new bugs / issues

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32d66f139ed6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.