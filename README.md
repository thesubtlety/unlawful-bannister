# unlawful-bannister

Testing malicious GitHub actions

## How things work 

- Workflows are defined in the repo path `.github/workflows/*`
- Can be started by an event, on schedule, or manually
- Can reference workflows from other workflows, can reuse secrets in those with: secrets: inherit
- Some events can be dangerous
  - if action executes the code in the pull request (e.g. auto build [i.e. execute code] on event)
  - Likely okay if PR is treated as data
- `pull_request_target` event gives the PR write access to repo and repo secrets
- Actions get a `GITHUB_TOKEN` with default read to the repo contents and metadata (can be changed) and nothing else. This token lasts for an hour
- Activity occurs on Github infrastructure

## Reference

- https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions
- https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows
- https://securitylab.github.com/research/github-actions-preventing-pwn-requests/
- https://cloud.hacktricks.xyz/pentesting-ci-cd/github-security#abusing-github-action
- https://medium.com/tinder/exploiting-github-actions-on-open-source-projects-5d93936d189f
