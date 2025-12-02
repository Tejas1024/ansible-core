# 3_ansible_adhoc_commands.md

# ✅ Ansible Ad-hoc Commands – Full Notes

---

## 1. What Are Ad-hoc Commands?

- One-line Ansible commands for **single-use** tasks.  
- No need to write a playbook.  
- Useful for:
  - Quick checks
  - One-time changes
  - Testing connectivity / modules [web:47][web:55]  

---

## 2. General Syntax

ansible <groupname> -i inventory -m <module> -a "<arguments>"

 

- `<groupname>` → group from inventory (e.g., `servers`)  
- `-i inventory` → inventory file path  
- `-m` → module (e.g., `ansible.builtin.file`)  
- `-a` → module arguments  

Common modules:

- `ansible.builtin.apt` → manage packages (Debian/Ubuntu) [web:49][web:57]  
- `ansible.builtin.file` → manage files/directories & permissions [web:50][web:58]  
- `ansible.builtin.service` → manage services [web:52][web:60]  
- `ansible.builtin.user` → manage users [web:51][web:59]  

---

## 3. Ad-hoc Command Examples (From Notes)

### 1️⃣ Change file permissions on all servers

ansible servers -i inventory -m ansible.builtin.file
-a "dest=/home/ubuntu/sample/a1.txt mode=650"

 

- Sets permissions of `/home/ubuntu/sample/a1.txt` to `650`.  

---

### 2️⃣ Change owner & group of file (with sudo)

ansible servers -i inventory -m ansible.builtin.file
-a "dest=/home/ubuntu/sample/a1.txt mode=600 owner=ubuntu group=devops" --become

 

- Sets:
  - owner → `ubuntu`  
  - group → `devops`  
  - mode → `600`  
- `--become` → elevate to root for ownership changes. [web:50][web:58]  

---

### 3️⃣ Create directory on all servers

ansible servers -i inventory -m ansible.builtin.file
-a "dest=/home/ubuntu/king mode=755 owner=ubuntu group=ubuntu state=directory"

 

- Creates `/home/ubuntu/king` directory with `755` permissions. [web:50][web:58]  

---

### 4️⃣ Install OpenJDK

ansible servers -i inventory -m ansible.builtin.apt
-a "name=openjdk-17-jdk state=present"

 

- Installs `openjdk-17-jdk` on all hosts in `servers`. [web:49]  

---

## 4. Playbook Concept Teaser (from bottom of notes)

Basic playbook structure:

name: <playbook-name>
hosts: <groupname>
become: yes
tasks:

name: <task-1>
<module>:
<params>

name: <task-2>
<module>:
<params>

 

Run with:

ansible-playbook -i inventory <playbook-file>.yaml

 

Ad-hoc → quick one-off command.  
Playbook → repeatable, structured automation. [web:48][web:56]  