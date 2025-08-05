# Home-Lab: Wazuh Security Monitoring

## Objective  
To set up a Wazuh home lab on an Ubuntu server for security monitoring and extend its functionality by adding a Wazuh agent on another Ubuntu server to monitor its logs and activities.

---

## Lab Setup    
![Blue and Gold Elegant Minimalist Jewelry Promotions Business Floor Decal (150 x 120 mm)](https://github.com/user-attachments/assets/ecfe331d-e276-4ee7-8012-e627e8a5677d)



## Requirements  
1. **Virtualization Tools:**  
   - [VirtualBox](https://www.virtualbox.org/)  
   - [VMware Workstation Pro](https://www.vmware.com/products/workstation-pro.html)  
   - [Proxmox VE](https://www.proxmox.com/)  

2. **Ubuntu Servers:**  
   - One server as the **Wazuh Manager** (20.04 or later).  
   - One server as the **Wazuh Agent** (20.04 or later).  

3. **Stable Internet Connection**  
4. **Sudo Privileges** on both Ubuntu servers.

---

## Step-by-Step Guide

### 1. **Set Up Wazuh Manager**  
   - Install and update the Ubuntu server for the manager role:  
     ```bash
     sudo apt update && sudo apt upgrade -y
     ```
   - Install Wazuh using the one-line command:  
     ```bash
     curl -sO https://packages.wazuh.com/4.9/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
     ```
   - Access the Wazuh Dashboard via a web browser:  
     ```
     https://<server-ip>:5601
     ```
   - Log in using the credentials displayed during the installation process.

### 2. **Set Up Wazuh Agent on Another Ubuntu Server**  
   - On the **second Ubuntu server**, update the packages:  
     ```bash
     sudo apt update && sudo apt upgrade -y
     ```
   - Install the Wazuh Agent using the following command:  
     ```bash
     curl -sO https://packages.wazuh.com/4.9/wazuh-agent.sh && sudo bash ./wazuh-agent.sh -a -s <WAZUH_MANAGER_IP>
     ```
   - Replace `<WAZUH_MANAGER_IP>` with the IP address of the Wazuh Manager server.  

### 3. **Configure Wazuh Agent**  
   - Open the agent configuration file:  
     ```bash
     sudo nano /var/ossec/etc/ossec.conf
     ```
   - Ensure the `<address>` tag contains the correct Wazuh Manager IP:  
     ```xml
     <address><WAZUH_MANAGER_IP></address>
     ```
   - Restart the agent to apply changes:  
     ```bash
     sudo systemctl restart wazuh-agent
     ```

### 4. **Verify Agent Connection on Wazuh Manager**  
   - Log in to the Wazuh Dashboard.  
   - Navigate to **Agents** under the **Management** tab.  
   - Confirm the agent appears in the list and is marked as **Active**.

---

## Conclusion  
This guide sets up a Wazuh Manager and extends its monitoring by adding a Wazuh agent on another Ubuntu server. This configuration allows centralized security monitoring, log analysis, and incident detection for multiple devices within your home lab. Experiment further by adding additional agents or customizing monitoring rules to enhance your security capabilities.
