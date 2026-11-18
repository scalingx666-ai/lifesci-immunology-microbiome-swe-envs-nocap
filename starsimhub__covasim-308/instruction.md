# Issue

**Title:** Add novavax brand to vaccine choices

## Description

This PR adds a new brand of vaccine: novavax, which is the third main brand Australia has planned to use ([approx 51M doses expected to be available towards the end of 2021. 
](https://www.health.gov.au/node/18777/australias-vaccine-agreements#:~:text=Australia%20has%20entered%20into%204,to%20be%20safe%20and%20effective.&text=Thursday%208%20April%202021%3A%20The,COVID%2D19%20vaccination%20program%20rollout.)). First batches of this vaccine are expected to be available towards the end of 2021. 

Effectiveness values drawn from : 
+ https://ir.novavax.com/news-releases/news-release-details/novavax-covid-19-vaccine-demonstrates-893-efficacy-uk-phase-3

To test this new brand, I ran simulations using as a base [`dev_test_vaccine_efficiency.py`](https://github.com/InstituteforDiseaseModeling/covasim/blob/master/tests/devtests/dev_test_vaccine_efficiency.py). 

The values in [`get_vaccine_strain_pars`](https://github.com/brain-modelling-group/covasim/blob/add-novavax/covasim/parameters.py#L465) where set so that one obtains the levels of effectiveness reported by the company (ie,~ 89% for wild strain; ~86% for b.1.1.7; ~49-60% for b.1.351; no data available for p1).  The main parameter I adjusted to obtain the baseline effectiveness of novavax was [`nab_init`](https://github.com/brain-modelling-group/covasim/blob/add-novavax/covasim/parameters.py#L525)
 
Let me know if I need to provide any additional info.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1426a7a3c855`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.