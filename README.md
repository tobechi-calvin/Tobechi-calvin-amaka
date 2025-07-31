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
```

📍 **Access Kibana at**:  
```
http://<ELK_SERVER_IP>:5601
```

---

### 2. 🚀 Install Fleet Server (on ELK Manager)
```bash
sudo apt install elastic-agent

# Replace with actual ELK server IP
sudo elastic-agent enroll --url=http://<ELK_SERVER_IP>:8220 --fleet-server-es=http://<ELK_SERVER_IP>:9200

sudo systemctl enable --now elastic-agent
```

---

### 3. 🤖 Install Fleet Agent on Second Ubuntu Server
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install elastic-agent

# Replace values with those from Kibana Fleet setup
sudo elastic-agent enroll --url=http://<FLEET_SERVER_IP>:8220 --enrollment-token=<ENROLLMENT_TOKEN>
```

---

### 4. ✅ Verify Agent Integration
- Log in to **Kibana**
- Navigate to `Fleet > Agents`
- Confirm new agent status is **Healthy**

---

### 5. 📄 Test Log Collection
- Generate test logs (system or application logs)
- Check **Kibana > Discover** for incoming data

---

## ✅ Conclusion
You now have a fully functional **centralized security log monitoring** setup with:
- ELK Stack (Elasticsearch, Logstash, Kibana)
- Fleet for scalable agent management  
This setup is ideal for learning **real-world SOC skills**, monitoring, and incident detection!

---

## 🌟 Ultimate Security Analyst Course

Get hands-on and master cybersecurity with our structured course:

- 🎥 **145+ Video Tutorials**
- 💻 **13 Hands-on Beginner Courses**
- 🛠 **90-Day Advanced Projects Challenge**
- 🤝 **Lifetime Community Access**
- 🏅 **Hall of Fame Recognition**

<a href="https://learn.haxsecurity.com/services/securitychallenge">
  <img src="https://img.shields.io/badge/-Enroll%20Now-008CBA?&style=for-the-badge&logo=Book&logoColor=white" alt="Enroll Now"/>
</a>

---

## 📂 License
This project is open-source and available for learning and educational purposes.

---

## 🙌 Contributions
Feel free to fork this repo, add more tools (e.g., Osquery, Zeek, Velociraptor), and submit a pull request!
