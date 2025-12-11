# Detection Portfolio — Vidit Talati

This repo hosts a small, focused portfolio of **behavioral detection** work and **signature detections** I've produced. It demonstrates the full lifecycle:
Threat Research → Sigma rule → Splunk translation → validation on sample logs → false positive tuning.

**What's inside**
- `sigma/` — Sigma rules (YAML) for Linux reverse shell, PowerShell encoded command, GitLab PAT admin-scope detection.
- `splunk/` — Splunk SPL equivalents for each Sigma rule and notes for tuning.
- `logs/` — Small synthetic sample logs to validate detections locally.
- `writeups/` — Short write-ups explaining attacker behaviour, detection rationale, false positives and tuning steps.
- `docs/` — Diagrams (attack flow, detection flow) — add PNGs here for visual presentation.

If you'd like to run these locally, see `sigma_to_splunk.md` for a quick validation guide.

---

## TL;DR — Key Detections
1. **Encoded PowerShell execution** — behavioral detection tuned with parent process and user allowlist.
2. **Suspicious reverse shell** — Linux process creation patterns for `nc`, `bash -i >& /dev/tcp/`, `python -c socket`.
3. **GitLab PAT created with admin scopes** — SaaS telemetry detection using audit logs and MFA/access context.

---

## Contact
Vidit Talati — vidittalati@gmail.com  
LinkedIn: https://www.linkedin.com/in/vidit-talati  
