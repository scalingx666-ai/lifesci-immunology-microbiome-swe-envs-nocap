# Issue

**Title:** [DevOps] adding readme for how to deploy elasticstack using helm charts

## Description

# Link to issue

- Related: 

# Changelog entry

- README on how to use helm to install elastic stack into an elastic-stack namespace in a k8s cluster. 

# Additional info

This has been deployed already for testing into the `test-es` namespace on preprod. This namespace can be deleted at anytime. 

I'd suggest a review of the available overrides for each helmchart to ensure that the right settings are getting set that meet the needs for this project. 

The default settings have been applied to each service in the Elastic Stack so far and that means:

* metricbeat is pulling metric data from all pods in all namespaces
* filebeat is pulling all logs from all pods in all namespaces
* kibana is running without an ingress, which means you need to configure port forwarding to access kibana
* elasticsearch has no default username/password (also there is no ingress so you must have port forwarding enabled to access elasticsearch). 
* AMP server is configured to connect to elasticsearch, but no data is being shipped to APM server yet. This is something that the CHIME app would need to be updated to support. 

---

## <center>Pull Request Checklist</center>

### <center>For Reviewer</center>

- [ ] Submitted under the correct tag
- [ ] Runs without error or warning
- [ ] Documentation  revised / included
- [ ] Unit tests included
- [ ] Issues referenced
- [ ] Does not create new bugs / issues

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `188c35be9561`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.