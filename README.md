# 🛡️ Tobechi Calvin Amaka – SOC Analyst Portfolio

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tobechi-calvin)
[![GitHub](https://img.shields.io/badge/GitHub-Profile-black?style=flat&logo=github)](https://github.com/tobechi-calvin)
[![Email](https://img.shields.io/badge/Email-Me-red?style=flat&logo=gmail)](mailto:tobechicalvin@gmail.com)
![Visitors](https://visitor-badge.laobi.icu/badge?page_id=tobechi-calvin.Mini-Soc-Home-Lab)

---

## 📂 Table of Contents

- [👋 About Me](#-about-me)
- [🚀 Featured Projects](#-featured-projects)
  - [📥 Phishing Triage Playbook](#-phishing-triage-playbook)
  - [📊 Splunk Security Dashboards](#-splunk-security-dashboards)
  - [🦠 Malware Analysis Lab](#-malware-analysis-lab)
  - [🎯 Threat Hunting with Splunk](#-threat-hunting-with-splunk)
  - [🚨 Incident Response Playbooks](#-incident-response-playbooks)
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

---

## 🚀 Featured Projects

### 📥 Phishing Triage Playbook

- ✅ JSON-based SOAR automation for phishing alert handling  
- 🔗 Integrates with VirusTotal, URLScan, and AbuseIPDB  
- 🧠 Includes decision trees and remediation logic

<details>
<summary>📄 Sample JSON Snippet</summary>

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
