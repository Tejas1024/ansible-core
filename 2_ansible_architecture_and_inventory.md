# 2_ansible_architecture_and_inventory.md

# ✅ Ansible Architecture & Inventory File

---

## 1. Ansible Architecture – Main Components

1️⃣ **Inventory File**

- Contains IPs or hostnames of all target servers.  
- Example:
  - `10.0.0.1`  
  - `10.0.0.2`  
  - `10.0.0.3`  
- Tells Ansible **which** machines to configure. [web:55]  

2️⃣ **Ansible Server / Control Node**

- Machine where Ansible is installed.  
- Responsibilities:
  - Reads inventory  
  - Runs Playbooks / ad-hoc commands  
  - Connects to servers via SSH/WinRM  
  - Installs/configures software on targets [web:41][web:42][web:43][web:53]  

3️⃣ **Playbook File**

- YAML file defining tasks:
  - install java  
  - install nginx  
  - install maven  
- Applied to hosts/groups from inventory. [web:48][web:56]  

**Flow**

- Install Ansible on control node.  
- Create:
  - Inventory file → list of servers  
  - Playbook → list of tasks  
- Ansible connects via SSH and executes tasks on each server.  

---

## 2. Setting Up Inventory – Step by Step (from notes)

### STEP 1 – Create EC2 instance for Ansible server

- OS: Ubuntu  
- Instance type: `t2.medium`  
- Create/download key pair  
- Launch instance  

### STEP 2 – Install Ansible on control node

sudo apt update
sudo apt install ansible -y

 

### STEP 3 – Create 2 more Ubuntu servers (targets)

- OS: Ubuntu  
- Instance type: `t2.medium`  
- Use **same key pair**  
- Launch instances  

### STEP 4 – Place key pair on Ansible server

- Create directory (e.g., `~/keys`)  
- Copy `.pem` file content into a file with same name  
- Set correct permissions:

chmod 400 <key-pair-name>.pem

 

### STEP 5 – Create inventory file

nano inventory

 

Add:

[servers]
<public-IP-server1>
<public-IP-server2>

[servers:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=/path/to/<key-pair-name>.pem

 

- `servers` → group name (can be any name)  
- `ansible_user=ubuntu` → default Ubuntu user  
- `ansible_ssh_private_key_file` → path to `.pem` key [web:46][web:54][web:55]  

### STEP 6 – Test connectivity with ping module

ansible servers -i inventory -m ping

 

- On success, response = `"pong"` from each host. [web:47][web:55]  

---

## 3. Architecture Summary

| Component      | Purpose                              |
|----------------|--------------------------------------|
| Inventory      | Target servers list                  |
| Playbook       | Tasks to execute                     |
| Control Node   | Runs Ansible & orchestrates changes  |
| Target Servers | Receive configuration via SSH       