# 🛡️ Tobechi Calvin Amaka – SOC Analyst Portfolio

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tobechi-calvin-79003925a/)
[![GitHub](https://img.shields.io/badge/GitHub-Profile-black?style=flat&logo=github)](https://github.com/tobechi-calvin)
[![Email](https://img.shields.io/badge/Email-Me-red?style=flat&logo=gmail)](mailto:tobechicalvin@gmail.com)
![Visitors](https://visitor-badge.laobi.icu/badge?page_id=tobechi-calvin.Mini-Soc-Home-Lab)

---

## 👋 About Me

Hi! I’m **Tobechi Calvin Amaka**, a **Tier 2 SOC Analyst** with **5+ years** of experience in:

- 🔍 Threat Detection  
- 🚨 Incident Response  
- 📧 Phishing Triage  
- 📊 Splunk Engineering  
- ⚙️ SOAR & Playbook Automation  
- 🔧 Splunk Administration

This portfolio highlights my real-world security engineering skills and practical SOC use cases.

---

## 🚀 Featured Projects

### 📥 Phishing Triage Playbook

- ✅ JSON-based SOAR automation for phishing alert handling  
- 🔗 Integrated with VirusTotal, URLScan, and AbuseIPDB  
- 🧠 Includes decision trees and remediation logic

**JSON Snippet:**

```json
{
  "playbook": {
    "name": "Phishing Triage",
    "steps": [
      {"action": "Extract indicators from email"},
      {"action": "Enrich IOCs using VirusTotal & URLScan"},
      {"action": "Check blocklists (AbuseIPDB, IPVoid)"},
      {"decision": "Is IOC malicious?"},
      {"action": "Quarantine email & reset user password if true"}
    ]
  }
}
📊 Splunk Security Dashboards
👀 Visualizations for brute force attacks, insider threats, and lateral movement

🛠️ Uses real-world SOC alert patterns

📸 Includes XML-based dashboard configuration examples

Splunk Query:

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
🦠 Malware Analysis Lab
🔬 Performed static and dynamic analysis in a sandbox environment

🧰 Created YARA rules to detect known malware behavior

📄 Wrote analysis reports on PE headers, API calls, and system behavior

Sample YARA Rule:

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
🎯 Threat Hunting with Splunk
🔎 Developed hunting queries aligned with MITRE ATT&CK framework

🎯 Focus areas include suspicious PowerShell, beaconing activity, and credential dumping (T1003)

Sample Query – Credential Dumping (T1003):

splunk
Copy
Edit
index=windows sourcetype=WinEventLog:Security EventCode=4624 LogonType=2 OR LogonType=10
| stats count by user, src_ip
🚨 Incident Response Playbooks (NIST 800-61)
📋 Built response playbooks following the NIST incident response lifecycle

📊 Includes flowcharts and SOPs for phishing, malware, and lateral movement incidents

NIST IR Lifecycle:

🛠️ Preparation

🚨 Detection & Analysis

🔐 Containment

🧹 Eradication

🔄 Recovery

📚 Post-Incident Review

🔧 Splunk Admin – L2 SOC Analyst Use Case
As a Level 2 SOC Analyst, I also handled Splunk Administration tasks to enhance visibility, maintain uptime, and accelerate threat response.

✅ Key Contributions:
🛠️ Installed and configured Splunk Enterprise and Universal Forwarders

📁 Built and maintained custom indexes, sourcetypes, and field extractions

🔄 Onboarded logs from Windows, Linux, Firewalls, EDRs, and Cloud

🧹 Tuned props.conf and transforms.conf for field parsing

🔐 Managed user roles and implemented least-privilege access on the search head

🧠 Used CIM to normalize data for correlation searches

📊 Scheduled alerts and maintained critical dashboards for Tier 1/Tier 2 teams

💼 Use Case: Detecting Lateral Movement
Objective: Detect unusual logins across internal assets

Steps:

Onboarded event logs from domain controllers

Normalized using CIM-compliant field names

Wrote query to catch rare LogonType=3 combinations by host/user

Built visual dashboard for user-IP login behavior

Triggered alert for excessive failed logins or rare sources

🛠️ Tools & Technologies
Category	Tools Used
SIEM & EDR	Splunk, CrowdStrike, QRadar
Vulnerability Mgmt	Nessus, Qualys
Threat Intelligence	VirusTotal, URLScan
Scripting & SOAR	Python, PowerShell, JSON-based Playbooks
Version Control	Git
Operating Systems	Windows, Linux (Ubuntu, CentOS)

📫 Contact
📧 Email: tobechicalvin@gmail.com
📍 Location: Dallas, TX
📞 Phone: 414-388-8044
🌐 GitHub: tobechi-calvin

This portfolio is actively maintained and reflects my growth as a cybersecurity professional. Thank you for visiting!
