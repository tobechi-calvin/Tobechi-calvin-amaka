# 🛡️ Mini SOC Home Lab on AWS with Elastic Stack

[![Elastic Stack](https://img.shields.io/badge/Elastic--Stack-7.17+-blue?logo=elastic)](https://www.elastic.co/)
[![AWS](https://img.shields.io/badge/Hosted%20on-AWS-FF9900?logo=amazon-aws&logoColor=white)](https://aws.amazon.com/)
[![Ubuntu](https://img.shields.io/badge/Linux-Ubuntu%2020.04-E95420?logo=ubuntu)](https://ubuntu.com/)
[![Windows](https://img.shields.io/badge/Windows-Server%202022-0078D6?logo=windows)](https://www.microsoft.com/)

---

This project showcases my ability to design, deploy, and monitor a **Security Operations Center (SOC) lab environment** in AWS using the **Elastic Stack (Elasticsearch, Kibana, and Fleet)**.  
It demonstrates hands-on skills in **cloud deployment, threat detection, log analysis, and incident response workflows**.

---

## 🔧 Project Overview
- Built a **fully functional SOC lab** in AWS with Ubuntu (Elastic Stack) and Windows Server endpoints.
- Configured **Elastic Agents** to forward logs into Elasticsearch via a Fleet Server.
- Enabled **real-time monitoring and visualization** of logs in Kibana.
- Integrated an **OS Ticket Server** to simulate incident triage.
- Simulated **attacker infrastructure (Kali Linux & C2 Server)** to test detection capabilities.

---

## 🧩 Architecture Summary
- **Elastic & Kibana**: Centralized log collection and visualization.
- **Fleet Server**: Manages Elastic Agents across endpoints.
- **Elastic Agents**: Installed on both Linux (SSH) and Windows (RDP) servers.
- **OS Ticket Server**: Simulates incident management workflows.
- **SOC Analyst Workstation**: Accesses Kibana dashboard via web GUI.
- **Attacker Infrastructure**: Kali Linux & C2 server for red-team simulations.

**VPC Configuration:**
- Private Subnet: `172.31.0.0/24`
- All services deployed on AWS EC2 instances.

📌**Architecture Diagram**
<img width="1040" height="853" alt="30 day challenge drawio - draw io" src="https://github.com/user-attachments/assets/a75aaf7f-5d79-436c-a764-5f93a4f5fec1" />


---

## ⚙️ Configuration & Setup Highlights
- ✅ Installed **Java 11 (OpenJDK)** for Elasticsearch/Kibana  
  <img width="806" height="93" alt="Java installed as the requirement to install elastic and kibana" src="https://github.com/user-attachments/assets/b96f6c9e-a71f-4fc1-942b-4cd9f5c0d60b" />
                          `Java installed as the requirement to install elastic and kibana`

- ✅ Deployed and validated services:
  - `elasticsearch.service` → **Active**
  - `kibana.service` → **Active**  
  <img width="1874" height="854" alt="Elastic and Kibana installed and running" src="https://github.com/user-attachments/assets/d78ad67c-009b-4c8e-996d-f8c8af7d4c2a" />
 `Elastic and Kibana installed and running`

- ✅ Configured AWS **Security Groups**:
  - 443 (HTTPS for Kibana)
  - 9200 (Elasticsearch REST API)
  - 22 (SSH), 3389 (RDP)  
  <img width="1883" height="817" alt="ModifyInboundSecurityGroupRules _ EC2 _ us-east-1" src="https://github.com/user-attachments/assets/11b98d8b-c3bd-4712-98c3-39fc4049d911" />
 
    - `ModifyInboundSecurityGroupRules _ EC2 _ us-east-1`  
    - `ModifyInboundSecurityGroupRules _ EC2 _ us-east-1_RDP`

- ✅ Verified data ingestion in Kibana Discover  
  
 `Elastic GUI`

- ✅ Created **Fleet Server** and enrolled agents:  
  - Windows Server (RDP)  
  - Ubuntu Server (SSH)  
  <img width="1919" height="979" alt="Agents - Fleet - Elastic" src="https://github.com/user-attachments/assets/26cdfd16-d68b-4500-912f-c18190843cca" />
 `Agents - Fleet - Elastic`

- ✅ Accessed Windows Server via RDP  
  <img width="1901" height="1056" alt="Remote Desktop Connection" src="https://github.com/user-attachments/assets/11f13106-2cee-4a35-841f-434202d3216c" />
 `Remote Desktop Connection`

---

## 🔍 Detection & Monitoring
- Monitored logs in **Kibana Discover** (`logs-*` index pattern).
- Validated ingestion of Windows Event Logs (e.g., Event ID 4624/4625) and Linux auth logs.
- Example monitored fields:
  - `agent.name`
  - `cloud.account.id`
  - `event.code`
  - `timestamp`
- Confirmed **agent-heartbeat and Fleet communication**.  

 `Discover - Elastic logs`

---

🧪 Next Phase – Attack Simulation & Detection

As part of extending my SOC Home Lab, I simulated attacker activity from Kali Linux against a Windows Server target and monitored detection within Elastic. This phase demonstrates practical offensive testing (Red Team) and defensive monitoring (Blue Team) workflows.

🔓 1. Brute-Force Simulation from Kali Linux

Using Crowbar from a Kali Linux machine, I launched a brute-force attack against the Windows Server’s RDP service.

📌Crowbar brute-force attempt on RDP
<img width="1920" height="656" alt="2025-08-18 14_32_08-KaliLinux2024  Running  - Oracle VM VirtualBox" src="https://github.com/user-attachments/assets/293333bb-d606-49da-8198-5a33edcf5ac2" />


Elastic map showing failed RDP logins from multiple geolocations

👉 Result: Elastic successfully logged failed RDP attempts across different IPs (US, Iran, Russia), confirming visibility into brute-force attempts.

🕵️ 2. Successful Intrusion & Post-Exploitation

After repeated attempts, the brute-force simulation resulted in a successful login. From Kali, I connected to the Windows Server via RDP and executed reconnaissance commands (whoami, ipconfig, net user administrator) to simulate persistence.

📌RDP connection from Kali
<img width="1916" height="1031" alt="2025-08-18 14_53_12- - Copy" src="https://github.com/user-attachments/assets/2c76d2c1-d355-4164-b715-03557a72456e" />

Successful login attempt with LogonType 10 & 7
Elastic detection of successful login event


👉 Result: Elastic captured Event ID 4624 with LogonType 10 (remote) and LogonType 7 (unlock), confirming attacker access and persistence.

📊 3. Detection in Elastic

I configured Elastic SIEM dashboards to monitor both failed and successful authentication attempts.

📌 Dashboard.png (SOC dashboard overview)

Discover - Elastic logs.png (raw failed/successful login events)

Successful login attempt with LogonType 10 & 7.png (highlighted detection logs)

👉 Result: Dashboards provided visibility into brute-force patterns, successful logons, and geographic anomalies.

🛡️ 4. SOC Analyst Investigation Workflow

The SOC triage process was tested using the simulated attack. Analysts can:

Identify failed login spikes from unusual geolocations.

Correlate with successful logons to detect potential compromise.

Escalate incidents to the OS Ticket system for further investigation.

📌 Failed login attempts from different locations.png (geo-view of failed logins)


Successful login attempt with LogonType 10 & 7.png (confirmation of successful intrusion)


👉 Result: Workflow validated the SOC’s ability to detect, investigate, and escalate brute-force and intrusion attempts.

✅ Key Takeaways

Elastic provided end-to-end visibility across brute-force attempts, successful logins, and post-exploitation activity.

Simulation validated Red Team vs Blue Team workflows in a controlled AWS SOC lab.

Next improvements include:

Automating detection rules for brute-force spikes.

Forwarding alerts to OS Ticket for incident triage.

Expanding detection use cases (reverse shell, persistence, privilege escalation).
** STAY TUNE**
