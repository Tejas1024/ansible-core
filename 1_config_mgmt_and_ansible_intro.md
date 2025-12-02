# 1_config_mgmt_and_ansible_intro.md

# ✅ Configuration Management & Ansible – Core Notes

---

## 1. Configuration Management

**Definition**

Configuration management ensures that all servers and environments are:

- Consistent  
- Correctly configured  
- Automatically updated (no manual per-server changes)  

Key benefits:

- Fully automated process  
- Consistency across servers  
- Flexible ways to update many servers  
- Improved efficiency and reliability [web:42]  

**Popular Configuration Management Tools**

- Ansible  
- Chef  
- Puppet  
- PowerShell DSC  
- SaltStack [web:42]  

---

## 2. Introduction to Ansible

**What is Ansible?**

- Open-source automation and configuration management tool [web:41][web:43][web:44][web:45][web:53]  
- Used for:
  - Installing software  
  - Configuring systems  
  - Managing multiple servers at once  

**History (from notes, corrected)**

- Created by Michael DeHaan (original author)  
- Project started around 2012; acquired by Red Hat later [web:53]  
- Quickly became a popular open-source automation project on GitHub  

---

## 3. Key Features of Ansible

- Free and open source [web:41][web:45]  
- Agentless architecture (no agents/slaves on target nodes) [web:41][web:42][web:44][web:45][web:53]  
- Uses SSH (Linux/Unix) and WinRM (Windows) for communication [web:41][web:42][web:44][web:45][web:53]  
- Uses **Inventory** files + **Playbooks** (YAML) [web:43][web:56]  
- Automates tasks across multiple servers in parallel [web:42][web:56]  
- Cross-platform: Linux, Windows, cloud platforms (AWS, etc.) [web:41][web:45]  
- Secure communication via SSH / WinRM  

---

## 4. Learning Flow (from your notes)

- Configuration Management  
- Introduction to Ansible  
- Inventory file creation  
- Ad-hoc commands  
- Playbooks  
- Ansible variables  
- Ansible modules  

This file covers the first two; next files cover architecture, inventory, adhoc, and playbooks.  
