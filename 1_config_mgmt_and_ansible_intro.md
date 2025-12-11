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
- Improved efficiency and reliability   

**Popular Configuration Management Tools**

- Ansible  
- Chef  
- Puppet  
- PowerShell DSC  
- SaltStack   

---

## 2. Introduction to Ansible

**What is Ansible?**

- Open-source automation and configuration management tool   
- Used for:
  - Installing software  
  - Configuring systems  
  - Managing multiple servers at once  

**History (from notes, corrected)**

- Created by Michael DeHaan (original author)  
- Project started around 2012; acquired by Red Hat later   
- Quickly became a popular open-source automation project on GitHub  

---

## 3. Key Features of Ansible

- Free and open source   
- Agentless architecture (no agents/slaves on target nodes)   
- Uses SSH (Linux/Unix) and WinRM (Windows) for communication   
- Uses **Inventory** files + **Playbooks** (YAML)   
- Automates tasks across multiple servers in parallel   
- Cross-platform: Linux, Windows, cloud platforms (AWS, etc.)   
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
