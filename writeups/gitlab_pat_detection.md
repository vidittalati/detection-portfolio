# GitLab PAT Admin Scope Detection — Writeup

## Summary
Detect personal access tokens created with high privileged scopes (e.g., api, sudo). Such tokens with admin scopes can be used for lateral movement and automation-based persistence.

## Attacker Behavior
- Adversary creates PAT with admin scopes, then uses it to call admin APIs (create projects/users, change settings).

## Detection Logic
- Audit log event `personal_access_token.created` where token scopes contain high privilege scopes.
- Correlate with user role — if non-admin user requests admin-scoped token, raise priority.
- Correlate with source IP reputation, recent logins, MFA failures.

## Sigma (refer to `sigma/gitlab-pat-admin-scope.yml`)
## Splunk (refer to `splunk/gitlab_pat_admin_scope.spl`)

## False Positives & Tuning
- Some automation requires admin-level tokens; maintain an allowlist of service accounts and known automation tokens.
- Use immediate activity (API calls using the token) to prioritize suspicious tokens.

## MITRE Mapping
- Credential Access / Persistence
