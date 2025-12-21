# Quick Guide: Converting Sigma to Splunk (Practical tips)

1. Identify the fields used in the Sigma detection (CommandLine, ParentImage, EventName, TokenScopes).
2. Map to Splunk sourcetypes in your environment (e.g., `linux:process`, `WinEventLog::ProcessCreation`, `gitlab:audit`).
3. Translate regex in Sigma to Splunk `match()` or `search` syntax (escape backslashes).
4. Add contextual enrichments: lookups (user allowlist), thresholds (count per host per time window), and parent process checks.
5. Validate on logs in `logs/` then tune allowlists and add clustering/time windows to reduce FP.
