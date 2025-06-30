# 🛡️ Mini SOC Home Lab on AWS with Elastic Stack

[![Elastic Stack](https://img.shields.io/badge/Elastic--Stack-7.17+-blue?logo=elastic)](https://www.elastic.co/)
[![AWS](https://img.shields.io/badge/Hosted%20on-AWS-FF9900?logo=amazon-aws&logoColor=white)](https://aws.amazon.com/)
[![Ubuntu](https://img.shields.io/badge/Linux-Ubuntu%2020.04-E95420?logo=ubuntu)](https://ubuntu.com/)
[![Windows](https://img.shields.io/badge/Windows-Server%202022-0078D6?logo=windows)](https://www.microsoft.com/)

---

## 🔧 Project Overview
As part of a hands, I designed and deployed a fully functional **Security Operations Center (SOC)** lab environment in AWS. This project demonstrates my ability to build, configure, and monitor infrastructure for real-time threat detection and log analysis using the **Elastic Stack (Elasticsearch, Kibana, and Fleet)**.

---

## 🧩 Architecture Summary
- **Elastic & Kibana**: Centralized log collection and visualization.
- **Fleet Server**: Manages Elastic Agents across endpoints.
- **Elastic Agents**: Deployed on both Linux (SSH) and Windows (RDP) servers to collect and forward logs.
- **OS Ticket Server**: Simulates incident management by receiving alert notifications.
- **SOC Analyst Workstation**: Accesses Kibana dashboard via web GUI.
- **Attacker Infrastructure (Kali & C2 Server)**: Simulates external threat actors for testing detection.

**VPC Configuration:**
- Private Subnet: `172.31.0.0/24`
- Elastic Stack and agents deployed within this network on AWS EC2 instances.

📌 **Network Diagram:**  
![30 day challenge drawio - draw io](https://github.com/user-attachments/assets/99405748-db0b-4dff-95fe-74e35777c400)

---

## ⚙️ Configuration & Setup Highlights

✅ **Installed Java 11 (OpenJDK)** to support Elasticsearch/Kibana  
📌 *Screenshot:*  
![Java installed as the requirement to install elastic and kibana](https://github.com/user-attachments/assets/1bf3b3db-0559-4e3b-91c1-06d6365fcca4)

---

✅ **Successfully deployed and validated services**:
- `elasticsearch.service` → ✅ *Active*
- `kibana.service` → ✅ *Active*

📌 *Screenshot:*  
![Elastic and Kibana installed and running](https://github.com/user-attachments/assets/159ce0a3-cb11-4a1a-8199-465ab8b5eeef)

---

✅ **Created a Fleet Server and enrolled agents from:**
- Windows Server (RDP)
- Ubuntu Server (SSH)

📌 *Screenshot:*  
![Agents - Fleet - Elastic](https://github.com/user-attachments/assets/c4f10688-dd0b-41bf-9c35-edda473dfcef)


---

✅ **Verified data ingestion on Kibana Discover**  
📌 *Screenshot:*  
![Discover - Elastic logs](https://github.com/user-attachments/assets/ae5a63dd-fbb2-456e-9a1e-05500b2ce50c)


---

✅ **Customized AWS Security Group rules** for ports:  
- `443` (HTTPS for Kibana)  
- `9200` (Elasticsearch REST API)  
- `22` (SSH), `3389` (RDP)

📌 *Inbound Rules for Elastic/Kibana/Ubuntu:*  
![ModifyInboundSecurityGroupRules _ EC2 _ us-east-1](https://github.com/user-attachments/assets/fa63b6ed-38c3-465c-bd7f-6df7ab139143)


📌 *Inbound Rules for RDP (Windows Server):*  
![ModifyInboundSecurityGroupRules _ EC2 _ us-east-1_RDP](https://github.com/user-attachments/assets/5ba3c992-aa22-41a6-ae13-0682f7908cdc)


---

✅ **Accessed Windows Server via RDP**  
📌 *Screenshot:*  
![Remote Desktop Connection](https://github.com/user-attachments/assets/aa1a2276-1f5e-4aa6-88d7-b90c5ffcd001)



---

## 🔍 Detection & Monitoring
- **Live log data visualization** through Kibana (`logs-*` index pattern)
- Monitored fields like `agent.name`, `cloud.account.id`, `timestamp`, etc.
- Elastic Agent logs confirm successful communication with the Fleet server

📌 *Screenshot:*  
![Elastic GUI](https://github.com/user-attachments/assets/090fb673-913d-4f9c-a908-25e10cdc88c8)
(Already shown above in “Kibana Logs View”)

---

## 🧪 Next Phase (Optional Enhancements)
- Simulate attacker activity from Kali Linux (e.g., reverse shell or brute force)
- Detect and alert on suspicious behavior using **Elastic Security**
- Forward alerts to the **OS Ticket System** for incident triaging
- Add ingest pipelines and detection rules via **Kibana Security Module**

---

## 📁 GitHub Repository
👉 _Coming Soon or [Insert your repo link]_

