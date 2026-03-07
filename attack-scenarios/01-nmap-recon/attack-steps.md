# Scenario 1 — Nmap Reconnaissance

## Attack Details
- **Date:** 07/03/2026
- **Attacker IP:** 192.168.100.10 (Kali)
- **Target IP:** 192.168.100.20 (Windows 10)
- **Tool:** Nmap
- **MITRE ATT&CK:** T1046 — Network Service Discovery

## Attack Commands
```bash
nmap -sV 192.168.100.20
```

## What Happened
Ran a service version scan against the Windows 10 victim machine.
Nmap probed all ports to identify running services.

## Wazuh Detection
- Total alerts generated: 401
- Alert spike visible on dashboard timeline
- MITRE ATT&CK technique mapped automatically

## Screenshots
- wazuh-alert-spike.png — Dashboard showing alert spike
- wazuh-event-detail.png — Individual alert details

## Incident Analysis
- **Severity:** Medium
- **Source:** 192.168.100.10 (Internal — Kali attacker VM)
- **Recommended Action:** Log source IP, monitor for follow-on exploitation attempts
