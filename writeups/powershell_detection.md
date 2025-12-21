# Encoded PowerShell Detection — Writeup

## Summary
Encoded PowerShell usage is commonly used for defense-evasion. This detection identifies processes executing PowerShell with `-EncodedCommand` or `-e` flags and augments detection with parent process context and allowlisting.

## Attacker Behavior
- Adversary launches encoded PowerShell via `cmd.exe` or via scheduled task.
- Encoded payloads hide malicious intentions and bypass simpler static rules.

## Detection Logic
- Identify PowerShell process with `-EncodedCommand` or `-e`.
- Ensure parent process is suspicious (explorer, cmd, wscript) and not known orchestration tools.
- Add allowlist (service accounts, orchestrator processes).

## Sigma (refer to `sigma/powershell-encoded-command.yml`)
## Splunk (refer to `splunk/powershell_encoded_command.spl`)

## False Positives & Tuning
- Legit automation may run encoded scripts — maintain `user_allowlist` and `parent_process_allowlist`.
- If automation accounts generate alerts, exclude them or add process lineage checks.

## MITRE Mapping
- Execution: T1059.001 (PowerShell)
- Defense Evasion: T1140 (Deobfuscate/Decode Files or Information)
