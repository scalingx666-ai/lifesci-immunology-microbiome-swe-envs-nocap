# Issue

**Title:** Added Behavioral Health Survey Component

## Description

Made a survey for behavioral component. On SurveyPage4.jsx
It contains 5 question and a rechart (npm install rechart) which displays the progress for the past few days. Currently both questions and the chart is rendered in the same page. It is right after the surveypage3. Also the current data for the chart is a sample data. 
Future edits: based on feedback:
1) initially we had the questions in a multi step form (one question at a time) but in order to math the flow of the health survey, the 5 behavioral questions are rendered on the same page. We can edit it based on the feedback we can get. 
2) the chart can also be loaded on a different page, so that the participant is not influenced by his/her previous progress. 

Furthermore: in response to the issue #267  for backend integration, we are in the midst of figuring out. 
1) how to send the data from these 5 questions to the backend:
2) how to fetch data from the previous entries in the backend to display on the chart. 
Please let me know if you have any questions, comments or suggestions. 

**Preliminary Changes for Backend**
-in reducers/survey.js --> added TO_SURVEY_PAGE_3 and SET_SURVEY_PAGE_4
-actions/actions.js --> added  toSurveyPage3, setSurveyPage4,
-observation.js --> under nonphysical, added interest, sadness, sleep, energy, appetite. 

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [ ] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ ] Have you added any new tests necessary?
- [x ] Is your PR rebased off the most current master?
- [x ] Have you squashed all commits, or if you will merge will you squash all commits?
- [ ] Did you use yarn, not npm?
- [ x] Did you use Material-UI wherever possible?
- [ x] Did you format according to Prettier?
- [ x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9349d1631ffb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.