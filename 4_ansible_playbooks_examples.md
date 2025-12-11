# 4_ansible_playbooks_examples.md

# ✅ Ansible Playbooks – Examples from Notes

---

## 1. Deploy Static Website to NGINX

Playbook actions:

1️⃣ Install nginx  
2️⃣ Start & enable nginx service  
3️⃣ Copy static site files to `/var/www/html`  

name: deploying static web host template in nginx
hosts: servers
become: yes

tasks:

name: Install nginx
ansible.builtin.apt:
name: nginx
state: present
update_cache: yes

name: Start and enable nginx service
ansible.builtin.service:
name: nginx
state: started
enabled: yes

name: Copy template files to nginx document root
ansible.builtin.copy:
src: /2150_living_parallax/
dest: /var/www/html
owner: ubuntu
group: ubuntu
mode: '704'

 

- Uses `apt` to install nginx and `service` to start/enable it.   

**Related SSH note from your notes:**

ssh -i "<key-pair-name>.pem" ubuntu@<other-instance-public-IP>

 

---

## 2. Create a User on All Servers

name: Creating users in ubuntu
hosts: servers
become: yes

tasks:

name: creating a user
ansible.builtin.user:
name: keithan
create_home: yes
shell: /bin/bash

 

- Uses `ansible.builtin.user` to create user `keithan` with home directory.   

---

## 3. Install Multiple Software Packages

Installs `curl`, `npm`, and `maven`:

name: Installing multiple softwares using playbook
hosts: servers
become: yes

tasks:

name: Installing multiple tools
ansible.builtin.apt:
name:
- curl
- npm
- maven
state: present

 

- Single task installing multiple packages via `apt`.   

---

## 4. Install & Enable MySQL

1️⃣ Install MySQL server  
2️⃣ Start and enable MySQL service  

name: Installing SQL and enabling it
hosts: servers
become: yes

tasks:

name: Installing SQL
ansible.builtin.apt:
name: mysql-server
state: present
update_cache: yes

name: Enabling SQL
ansible.builtin.service:
name: mysql
state: started
enabled: yes

 

**After installation (from notes):**

sudo mysql -u root -p

password: 123 # (local lab example)
 

---

## 5. Run Any Playbook

ansible-playbook -i inventory <playbook-name>.yaml

 

- Executes tasks sequentially against all hosts in specified inventory group.   

---

## 6. Ad-hoc vs Playbook (from notes)

| Feature   | Ad-hoc Command                 | Playbook                          |
|-----------|--------------------------------|-----------------------------------|
| Use case  | One-time / quick task         | Repeatable, structured automation |
| Format    | CLI command                   | YAML file                         |
| Best for  | Testing, small changes        | Full deployments / workflows      |
| Reusable  | No                             | Yes                               |  
