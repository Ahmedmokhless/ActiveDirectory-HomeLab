# 🖥️ Active Directory Home Lab Project

This repository documents my **Active Directory (AD) home lab project**, where I built a small enterprise-like environment inside VMware using **Windows Server 2019** and **Windows 10 Enterprise**.

---

## 🔹 Lab Setup
- **Hypervisor:** VMware Workstation  
- **Server OS:** Windows Server 2019 (with Desktop Experience)  
- **Client OS:** Windows 10 Enterprise  
- **Network:** Host-only (Private LAN)  
- **Domain Name:** `Project.local`  

---

## 🔹 Implementation Steps

### 1. Preparing the Environment
- Installed VMware and required ISOs (Windows Server 2019, Windows 10).  
- Created VM for **Primary Domain Controller (PDC)** with 4 GB RAM and static IP `192.168.1.2`.  
- Installed **VMware Tools** for better performance and resolution.  

![Domain Setup](screenshots/domain_setup.png)

---

### 2. Domain Controller Configuration
- Promoted server to **Domain Controller**.  
- Created new forest: `Project.local`.  
- Configured DSRM password and verified promotion.  

---

### 3. Organizational Units & Users
- Created OUs: **HR**, **IT**, **Sales**.  
- Automated user creation with **PowerShell + CSV**.  
- Created department security groups and added users.  

![OU and Users](screenshots/ou_users.png)

---

### 4. Group Policy Objects (GPOs)
- Created GPO to **disable Control Panel** for Sales users.  
- Tested with a Windows 10 client:  
  - IT user → full access  
  - Sales user → Control Panel restricted  

![GPO Sales Restriction](screenshots/gpo_sales.png)

---

### 5. File Sharing & FSRM
- Configured **shared folders** for each department with NTFS permissions.  
- Installed **File Server Resource Manager (FSRM)**.  
- Applied quotas (e.g., Sales folder limited to 2GB with warnings).  
- Configured file screening to block media files.  

![Shared Folders](screenshots/shared_folders.png)

---

### 6. DHCP Configuration & Failover
- Configured DHCP scope: `192.168.1.50 – 192.168.1.200`.  
- Added gateway `192.168.1.1` and DNS `192.168.1.2`.  
- Created a second server (**DHCP2**) for failover.  
- Tested → clients successfully received IPs when PDC DHCP was offline.  

![DHCP Failover](screenshots/dhcp_failover.png)

---

### 7. Windows Deployment Services (WDS)
- Installed and configured **WDS**.  
- Added boot/install images from Windows 10 ISO.  
- Created **autounattend.xml** with WSIM for automated deployment.  
- Tested → new client VM installed Windows 10 and joined domain automatically.  

![WDS Deployment](screenshots/wds_deployment.png)

---

### 8. Backup & Restore
- Installed **Windows Server Backup**.  
- Configured backup to secondary DC.  
- Successfully tested backup and restore by deleting/restoring files.  

![Backup](screenshots/backup.png)

---

## 🔹 Outcome
This project successfully simulated a small enterprise IT infrastructure.  
Key services implemented:  
- Active Directory Domain Services (AD DS)  
- Organizational Units & User Management  
- Group Policy Objects (GPOs)  
- File Server Resource Manager (FSRM)  
- DHCP with Failover  
- Windows Deployment Services (WDS)  
- Backup & Restore  

---

## 🔹 Key Learnings
- Gained practical experience with **enterprise-grade IT services**.  
- Learned how **automation** (PowerShell, WDS) simplifies administration.  
- Understood the importance of **redundancy** (DHCP failover).  
- Practiced **real-world security & access control** via GPOs and FSRM.  

---

## 🔹 Next Steps
- Extend the lab with **PKI / Certificate Services**.  
- Add **monitoring/logging** (SIEM integration).  
- Explore **multi-site domain replication**.  

---

## 🔹 Author
👤 **Ahmed Mokhless**  
🔗 [LinkedIn](https://www.linkedin.com/)  
🔗 [GitHub](https://github.com/)  

---
