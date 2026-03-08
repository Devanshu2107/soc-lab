# SOC Analysis Lab

![Status](https://img.shields.io/badge/Status-Active-success)
![SIEM](https://img.shields.io/badge/SIEM-Wazuh-blue)
![ATT&CK](https://img.shields.io/badge/Framework-MITRE%20ATT%26CK-red)

## Overview
A personal security operations lab for practising threat detection, 
log analysis and incident response. Documents real attack simulations 
and the detection engineering behind them.

## Environment
| Component | Details |
|---|---|
| SIEM | Wazuh 4.7 |
| Endpoint | Windows 10 + Sysmon |
| Attacker | Kali Linux |
| Framework | MITRE ATT&CK |

## Detection Scenarios
| # | Scenario | Tool | MITRE ATT&CK | Status |
|---|---|---|---|---|
| 1 | Network Reconnaissance | Nmap | T1046 | ✅ Complete |
| 2 | Brute Force Attack | Hydra | T1110 | 🔨 In Progress |
| 3 | Remote Code Execution | Metasploit | T1210 | 🔨 In Progress |
| 4 | Persistence via Scheduled Task | Msfvenom | T1053 | 🔨 In Progress |
| 5 | PowerShell Obfuscation | Msfvenom | T1059 | 🔨 In Progress |

## Scenario 1: Nmap Reconnaissance

###  Interactive Attack Flow Diagram

**[View Interactive Diagram](https://devanshu2107.github.io/soc-lab/attack-scenarios/01-nmap-recon/scenario1-rtbt-diagram.html)** 

This diagram shows the complete Red Team attack and Blue Team defense flow.

## Detection Engineering
Custom Wazuh rules written to detect each attack pattern,
mapped to MITRE ATT&CK techniques. See `siem-rules/` folder.

## Incident Reports
Each scenario includes a full incident report documenting:
- Attack timeline
- IOCs identified
- MITRE ATT&CK mapping
- Recommended remediation

## Tools Used
- Wazuh SIEM
- Sysmon + SwiftOnSecurity ruleset
- Kali Linux
- Nmap, Hydra, Metasploit
