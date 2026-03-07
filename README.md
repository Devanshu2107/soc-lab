# SOC Home Lab

![Status](https://img.shields.io/badge/Status-Active-success)
![SIEM](https://img.shields.io/badge/SIEM-Wazuh-blue)

## Overview
A hands-on SOC home lab built to simulate real-world attack and detection scenarios.
Built to demonstrate practical SOC analyst skills for job applications.

**Stack:** Wazuh SIEM | Kali Linux | Windows 10 | Sysmon

## Lab Architecture
| VM | IP | Role |
|---|---|---|
| Kali Linux | 192.168.100.10 | Attacker |
| Windows 10 | 192.168.100.20 | Victim endpoint |
| Wazuh SIEM | 192.168.100.40 | Detection & monitoring |

## Attack Scenarios
| # | Scenario | Tool | MITRE ATT&CK | Status |
|---|---|---|---|---|
| 1 | Nmap Port Scan | Nmap | T1046 | ✅ Complete |
| 2 | Brute Force | Hydra | T1110 | 🔨 In Progress |
| 3 | Metasploit RCE | Metasploit | T1210 | 🔨 In Progress |
| 4 | Windows Persistence | Msfvenom | T1053 | 🔨 In Progress |
| 5 | PowerShell Obfuscation | Msfvenom | T1059 | 🔨 In Progress |

## Skills Demonstrated
- Threat detection and log analysis (Wazuh SIEM)
- Custom SIEM rule writing (detection engineering)
- Attack simulation using offensive security tools
- Incident documentation and reporting
- Sysmon deployment and configuration

## Setup Guide
See individual folders for step-by-step documentation.
