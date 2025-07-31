# 🛡️ Security Monitoring Home Lab with ELK Stack + Fleet

## 🎯 Objective  
Set up a **Security Monitoring Home Lab** using the **ELK Stack** (Elasticsearch, Logstash, Kibana) for centralized log analysis and monitoring, and extend its functionality by integrating **Fleet** to manage agents on other servers.

---

## 🧰 Requirements  
### Virtualization Tools (Choose One)
- [VirtualBox](https://www.virtualbox.org/)
- [VMware Workstation Pro](https://www.vmware.com/products/workstation-pro.html)
- [Proxmox VE](https://www.proxmox.com/)

### System Setup
- **2 Ubuntu 20.04+ servers**
  - **ELK Stack Manager**
  - **Fleet Agent Node**
- **Stable Internet Connection**
- **Sudo privileges** on both servers

---

## ⚙️ Step-by-Step Setup

### 1. 🔧 Install ELK Stack on ELK Manager
```bash
sudo apt update && sudo apt upgrade -y

# Install Elasticsearch
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt install apt-transport-https
echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-8.x.list
sudo apt update && sudo apt install elasticsearch

# Enable Elasticsearch
sudo systemctl enable --now elasticsearch

# Install and start Kibana
sudo apt install kibana
sudo systemctl enable --now kibana
