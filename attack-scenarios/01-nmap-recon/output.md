  Scenario 1 — Nmap Reconnaissance Attack Flow @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;600;700&display=swap'); :root { --bg: #060a0f; --panel: #0b1117; --border: #1a2a3a; --red: #ff2d55; --blue: #00cfff; --green: #00ff9f; --yellow: #ffd60a; --orange: #ff6b2b; --text: #c8d8e8; --dim: #4a6a8a; } \* { margin: 0; padding: 0; box-sizing: border-box; } body { background: var(--bg); font-family: 'Rajdhani', sans-serif; color: var(--text); min-height: 100vh; padding: 40px 20px; overflow-x: hidden; } body::before { content: ''; position: fixed; inset: 0; background: radial-gradient(ellipse 80% 50% at 20% 20%, rgba(0,207,255,0.04) 0%, transparent 60%), radial-gradient(ellipse 60% 40% at 80% 80%, rgba(255,45,85,0.04) 0%, transparent 60%); pointer-events: none; } .header { text-align: center; margin-bottom: 50px; } .scenario-tag { display: inline-block; font-family: 'Share Tech Mono', monospace; font-size: 11px; color: var(--blue); border: 1px solid var(--blue); padding: 4px 14px; letter-spacing: 3px; margin-bottom: 16px; animation: pulse-border 2s ease-in-out infinite; } @keyframes pulse-border { 0%, 100% { border-color: var(--blue); box-shadow: 0 0 8px rgba(0,207,255,0.3); } 50% { border-color: rgba(0,207,255,0.4); box-shadow: none; } } h1 { font-size: 36px; font-weight: 700; letter-spacing: 2px; color: #fff; margin-bottom: 8px; } h1 span { color: var(--blue); } .subtitle { font-family: 'Share Tech Mono', monospace; font-size: 12px; color: var(--dim); letter-spacing: 2px; } /\* MITRE badge \*/ .mitre { display: inline-flex; align-items: center; gap: 8px; background: rgba(255,214,10,0.08); border: 1px solid rgba(255,214,10,0.3); padding: 6px 16px; border-radius: 2px; margin-top: 16px; font-family: 'Share Tech Mono', monospace; font-size: 12px; color: var(--yellow); } /\* Main flow container \*/ .flow { max-width: 1100px; margin: 0 auto; position: relative; } /\* Timeline line \*/ .timeline-line { position: absolute; left: 50%; top: 0; bottom: 0; width: 2px; background: linear-gradient(to bottom, transparent, var(--border) 10%, var(--border) 90%, transparent); transform: translateX(-50%); } .step { display: flex; align-items: flex-start; gap: 30px; margin-bottom: 40px; position: relative; animation: fadeIn 0.5s ease forwards; opacity: 0; } .step:nth-child(1) { animation-delay: 0.1s; } .step:nth-child(2) { animation-delay: 0.2s; } .step:nth-child(3) { animation-delay: 0.3s; } .step:nth-child(4) { animation-delay: 0.4s; } .step:nth-child(5) { animation-delay: 0.5s; } .step:nth-child(6) { animation-delay: 0.6s; } @keyframes fadeIn { to { opacity: 1; transform: translateY(0); } from { opacity: 0; transform: translateY(20px); } } .step-left { flex: 1; text-align: right; } .step-right { flex: 1; } .step-center { display: flex; flex-direction: column; align-items: center; gap: 8px; flex-shrink: 0; } .step-number { width: 44px; height: 44px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-family: 'Share Tech Mono', monospace; font-size: 16px; font-weight: bold; position: relative; z-index: 2; } .step-connector { width: 2px; height: 40px; background: var(--border); } .card { background: var(--panel); border: 1px solid var(--border); padding: 20px; position: relative; transition: border-color 0.3s; } .card:hover { border-color: var(--blue); } .card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; } .card-tag { font-family: 'Share Tech Mono', monospace; font-size: 10px; letter-spacing: 2px; margin-bottom: 8px; } .card h3 { font-size: 18px; font-weight: 700; letter-spacing: 1px; margin-bottom: 8px; color: #fff; } .card p { font-size: 14px; color: var(--text); line-height: 1.6; } .code-block { background: #040810; border: 1px solid var(--border); border-left: 3px solid var(--blue); padding: 10px 14px; margin-top: 12px; font-family: 'Share Tech Mono', monospace; font-size: 12px; color: var(--green); overflow-x: auto; } .badge { display: inline-block; padding: 3px 10px; font-family: 'Share Tech Mono', monospace; font-size: 10px; letter-spacing: 1px; margin-top: 10px; border-radius: 2px; } /\* Step-specific colors \*/ .step-attacker .step-number { background: rgba(255,45,85,0.15); border: 2px solid var(--red); color: var(--red); } .step-attacker .card::before { background: var(--red); } .step-attacker .card-tag { color: var(--red); } .step-scan .step-number { background: rgba(255,107,43,0.15); border: 2px solid var(--orange); color: var(--orange); } .step-scan .card::before { background: var(--orange); } .step-scan .card-tag { color: var(--orange); } .step-target .step-number { background: rgba(255,214,10,0.15); border: 2px solid var(--yellow); color: var(--yellow); } .step-target .card::before { background: var(--yellow); } .step-target .card-tag { color: var(--yellow); } .step-sysmon .step-number { background: rgba(0,207,255,0.15); border: 2px solid var(--blue); color: var(--blue); } .step-sysmon .card::before { background: var(--blue); } .step-sysmon .card-tag { color: var(--blue); } .step-wazuh .step-number { background: rgba(0,255,159,0.15); border: 2px solid var(--green); color: var(--green); } .step-wazuh .card::before { background: var(--green); } .step-wazuh .card-tag { color: var(--green); } .step-alert .step-number { background: rgba(0,255,159,0.15); border: 2px solid var(--green); color: var(--green); } .step-alert .card::before { background: var(--green); } .step-alert .card-tag { color: var(--green); } /\* Network diagram at top \*/ .network-diagram { display: flex; align-items: center; justify-content: center; gap: 0; margin-bottom: 60px; flex-wrap: wrap; } .node { display: flex; flex-direction: column; align-items: center; gap: 10px; } .node-icon { width: 80px; height: 80px; border-radius: 8px; display: flex; align-items: center; justify-content: center; font-size: 32px; position: relative; } .node-label { font-family: 'Share Tech Mono', monospace; font-size: 11px; text-align: center; letter-spacing: 1px; } .node-ip { font-size: 10px; color: var(--dim); } .arrow { display: flex; flex-direction: column; align-items: center; padding: 0 10px; gap: 4px; margin-top: -20px; } .arrow-line { height: 2px; width: 80px; position: relative; } .arrow-line::after { content: '►'; position: absolute; right: -8px; top: -9px; font-size: 12px; } .arrow-label { font-family: 'Share Tech Mono', monospace; font-size: 9px; letter-spacing: 1px; white-space: nowrap; } /\* Alert stats \*/ .stats-row { display: flex; gap: 20px; margin-top: 14px; flex-wrap: wrap; } .stat { display: flex; flex-direction: column; gap: 2px; } .stat-value { font-family: 'Share Tech Mono', monospace; font-size: 22px; font-weight: bold; } .stat-label { font-family: 'Share Tech Mono', monospace; font-size: 9px; color: var(--dim); letter-spacing: 1px; } /\* Bottom summary \*/ .summary { max-width: 1100px; margin: 40px auto 0; display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 16px; } .summary-card { background: var(--panel); border: 1px solid var(--border); padding: 20px; text-align: center; } .summary-card .label { font-family: 'Share Tech Mono', monospace; font-size: 10px; color: var(--dim); letter-spacing: 2px; margin-bottom: 8px; } .summary-card .value { font-size: 16px; font-weight: 700; color: #fff; } .tag-red { background: rgba(255,45,85,0.15); color: var(--red); border: 1px solid rgba(255,45,85,0.3); } .tag-green { background: rgba(0,255,159,0.15); color: var(--green); border: 1px solid rgba(0,255,159,0.3); } .tag-blue { background: rgba(0,207,255,0.15); color: var(--blue); border: 1px solid rgba(0,207,255,0.3); } .tag-yellow { background: rgba(255,214,10,0.15); color: var(--yellow); border: 1px solid rgba(255,214,10,0.3); } .scan-animation { display: inline-block; animation: scanPulse 1.5s ease-in-out infinite; } @keyframes scanPulse { 0%, 100% { opacity: 1; } 50% { opacity: 0.3; } } hr.divider { border: none; border-top: 1px solid var(--border); margin: 50px auto; max-width: 1100px; }

SCENARIO 01 // ATTACK FLOW

Nmap Reconnaissance
===================

NETWORK SERVICE DISCOVERY · DETECTION ANALYSIS

  

⚡ MITRE ATT&CK — T1046 · Network Service Discovery · Tactic: Discovery

💻

KALI LINUX  
192.168.100.10

ATTACKER

                    ►

NMAP SCAN PACKETS

TCP SYN · Port Probing

🖥️

WINDOWS 10  
192.168.100.20

TARGET

                    ►

SYSMON + WAZUH AGENT

Log Forwarding

🛡️

WAZUH SIEM  
192.168.100.40

DETECTION

PHASE 1 · ATTACKER

### Reconnaissance Initiated

Attacker on Kali Linux launches an Nmap service version scan targeting the Windows 10 victim machine on the isolated VMnet2 network.

nmap -sV 192.168.100.20

192.168.100.10 → 192.168.100.20

1

2

PHASE 2 · NETWORK

### Port Probe Packets Sent

Nmap sends TCP SYN packets across all ports probing for open services. Each packet hits Windows 10 generating network events.

TCP SYN → Port 21 (FTP)  
TCP SYN → Port 22 (SSH)  
TCP SYN → Port 80 (HTTP)  
TCP SYN → Port 445 (SMB)  
TCP SYN → Port 3389 (RDP)  
■ Scanning 65535 ports...

HIGH VOLUME · SEQUENTIAL PORTS

PHASE 3 · VICTIM ENDPOINT

### Windows 10 Receives Probes

Windows 10 receives the port probes. Sysmon (with SwiftOnSecurity ruleset) detects the unusual network connection patterns and logs Event ID 3 — Network Connection events.

Event ID 3: Network Connection  
SourceIp: 192.168.100.10  
DestinationPort: \[multiple\]  
Image: System

SYSMON EVENT ID 3 · NETWORK CONNECTION

3

4

PHASE 4 · LOG FORWARDING

### Wazuh Agent Forwards Logs

Wazuh Agent running on Windows 10 collects Sysmon events and Windows Event Logs in real-time and forwards them to the Wazuh Manager at 192.168.100.40.

Wazuh Agent → Wazuh Manager  
Protocol: TCP 1514  
Format: JSON encoded events  
Agent: Win10-victim (Active)

REAL-TIME LOG STREAMING

PHASE 5 · SIEM DETECTION

### Wazuh Raises 401 Alerts

Wazuh Manager processes incoming logs against its ruleset. The high volume of connection attempts from a single source IP triggers port scan detection rules.

Rule 40111: Multiple connection attempts  
Rule Level: 7 (Medium-High)  
Source IP: 192.168.100.10  
Agent: Win10-victim  
Total Alerts: 401

401 TOTAL ALERTS

7 RULE LEVEL

~60s TIMEFRAME

5

6

PHASE 6 · ANALYST RESPONSE

### SOC Analyst Investigates

SOC analyst opens Wazuh dashboard, identifies the alert spike, correlates source IP, checks MITRE ATT&CK mapping, and documents findings in an incident report.

MITRE ATT&CK: T1046  
Tactic: Discovery  
Technique: Network Service Discovery  
Severity: MEDIUM  
Action: Monitor for follow-on exploitation

✓ DETECTED · DOCUMENTED · REPORTED

* * *

ATTACK TOOL

Nmap -sV

ATTACKER IP

192.168.100.10

TARGET IP

192.168.100.20

ALERTS GENERATED

401

MITRE TECHNIQUE

T1046

DETECTION STATUS

✓ DETECTED

SEVERITY

MEDIUM

NETWORK

VMnet2 Isolated

SOC HOME LAB · github.com/Devanshu2107/soc-lab · SCENARIO 01 OF 05