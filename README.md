# 🛡️ Tobechi Calvin Amaka – SOC Analyst Portfolio

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tobechi-calvin-79003925a/)
[![GitHub](https://img.shields.io/badge/GitHub-Profile-black?style=flat&logo=github)](https://github.com/tobechi-calvin)
[![Email](https://img.shields.io/badge/Email-Me-red?style=flat&logo=gmail)](mailto:tobechicalvin@gmail.com)
![Visitors](https://visitor-badge.laobi.icu/badge?page_id=tobechi-calvin.Mini-Soc-Home-Lab)

---

## 📂 Table of Contents

- [👋 About Me](#-about-me)
- [🚀 Featured Projects](#-Featured-Projects)
  - [📥 Phishing Triage Playbook](#-phishing-triage-playbook)
  - [📊 Splunk Security Dashboards](#-splunk-security-dashboards)
  - [🦠 Malware Analysis Lab](#-malware-analysis-lab)
  - [🎯 Threat Hunting with Splunk](#-threat-hunting-with-splunk)
  - [🚨 Incident Response Playbooks](#-incident-response-playbooks)
  - [🔧 Splunk Admin – L2 SOC Analyst Use Case](#-splunk-admin--l2-soc-analyst-use-case)
- [🛠️ Tools & Technologies](#️-tools--technologies)
- [📫 Contact](#-contact)

---

## 👋 About Me

Hi! I’m **Tobechi Calvin Amaka**, a **Tier 2 SOC Analyst** with **5+ years** of experience in:

- 🔍 Threat Detection  
- 🚨 Incident Response  
- 📧 Phishing Triage  
- 📊 Splunk Engineering  
- ⚙️ SOAR & Playbook Automation

This portfolio highlights my real-world security engineering skills and practical SOC use cases.

## 🚀 Featured Projects

---

### 📥 Phishing Triage Playbook

- ✅ JSON-based SOAR automation for phishing alert handling  
- 🔗 Integrates with VirusTotal, URLScan, and AbuseIPDB  
- 🧠 Includes decision trees and remediation logic

<details>
<summary>📄 Sample JSON Snippet</summary>

json
{
  "playbook": {
    "name": "Phishing Triage",
    "steps": [
      {"action": "Extract indicators from email"},
      {"action": "Enrich IOCs using VirusTotal & URLScan"},
      {"action": "Check blocklists (AbuseIPDB, IPVoid)"},
      {"decision": "Is IOC malicious?"},
      {"action": "Quarantine email & reset user password if true"}
  }
}
</details>

📊 Splunk Security Dashboards
👀 Visualizations for brute force, insider threats, and lateral movement

🛠️ Uses real-world SOC alert patterns

📸 Includes XML samples and screenshots

<details> <summary>📄 Sample Splunk Query</summary>
xml
Copy
Edit
<dashboard>
  <label>Brute Force Detection</label>
  <row>
    <panel>
      <chart>
        <search>
          <query>index=auth sourcetype=linux_secure "authentication failure" | stats count by user, src_ip</query>
        </search>
        <title>Failed Login Attempts by Source</title>
      </chart>
    </panel>
  </row>
</dashboard>
</details>
🦠 Malware Analysis Lab
🔬 Conducted static and dynamic analysis in sandbox environments

🧰 Wrote custom YARA rules for malware behavior detection

<details> <summary>📄 Sample YARA Rule</summary>
yara
Copy
Edit
rule TrickBot_Example {
  meta:
    description = "Detect TrickBot executable"
    author = "Tobechi Amaka"
  strings:
    $s1 = "This program cannot be run in DOS mode"
    $s2 = "GetProcAddress"
    $s3 = "kernel32.dll"
  condition:
    all of ($s*)
}
</details>
🎯 Threat Hunting with Splunk
🔎 Created queries mapped to MITRE ATT&CK

🎯 Use cases: PowerShell abuse, beaconing, credential dumping (T1003)

<details> <summary>📄 Credential Dumping (T1003)</summary>
splunk
Copy
Edit
index=windows sourcetype=WinEventLog:Security EventCode=4624 LogonType=2 OR LogonType=10
| stats count by user, src_ip
</details>
🚨 Incident Response Playbooks
📋 Based on NIST 800-61

Includes visual workflows and escalation paths

Lifecycle:

🛠️ Preparation

🚨 Detection & Analysis

🔐 Containment

🧹 Eradication

🔄 Recovery

📚 Post-Incident Review

🔧 Splunk Admin – L2 SOC Analyst Use Case
As a Level 2 SOC Analyst, I also handled Splunk Administration tasks to improve security visibility and streamline incident response.

✅ Key Contributions:
🔄 Onboarded security logs (Windows, Linux, EDR, firewalls, proxies)

📁 Built custom indexes, sourcetypes, and field extractions

🧹 Tuned props.conf and transforms.conf for log parsing

🔐 Managed roles and access controls for search heads

🧠 Used CIM to normalize logs for correlation and threat detection

📊 Optimized dashboard performance and scheduled search alerts

💼 Real-World Example:
Goal: Detect lateral movement through network logon attempts.

Steps:

Onboarded logs from Windows event sources via Universal Forwarders

Normalized fields using CIM

Created search queries for LogonType=3 with rare src_ip + user combo

Built dashboard visualizing spike in failed logins by host/IP

Alert triggered to notify team of unusual activity in real-time

🛠️ Tools & Technologies
Category	Tools Used
SIEM & EDR	Splunk, CrowdStrike, QRadar
Vulnerability Mgmt	Nessus, Qualys
Threat Intel	VirusTotal, URLScan
Scripting & SOAR	Python, PowerShell, JSON-based Playbooks
Version Control	Git

📫 Contact
📧 Email: tobechicalvin@gmail.com
📍 Location: Dallas, TX
📞 Phone: 414-388-8044
🌐 GitHub: tobechi-calvin

This portfolio is continuously updated as I grow in the cybersecurity field. Thank you for visiting!
