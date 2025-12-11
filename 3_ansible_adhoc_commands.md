# 3_ansible_adhoc_commands.md

# ✅ Ansible Ad-hoc Commands – Full Notes

---

## 1. What Are Ad-hoc Commands?

- One-line Ansible commands for **single-use** tasks.  
- No need to write a playbook.  
- Useful for:
  - Quick checks
  - One-time changes
  - Testing connectivity / modules   

---

## 2. General Syntax

ansible <groupname> -i inventory -m <module> -a "<arguments>"

 

- `<groupname>` → group from inventory (e.g., `servers`)  
- `-i inventory` → inventory file path  
- `-m` → module (e.g., `ansible.builtin.file`)  
- `-a` → module arguments  

Common modules:

- `ansible.builtin.apt` → manage packages (Debian/Ubuntu)   
- `ansible.builtin.file` → manage files/directories & permissions   
- `ansible.builtin.service` → manage services   
- `ansible.builtin.user` → manage users   

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
- `--become` → elevate to root for ownership changes.   

---

### 3️⃣ Create directory on all servers

ansible servers -i inventory -m ansible.builtin.file
-a "dest=/home/ubuntu/king mode=755 owner=ubuntu group=ubuntu state=directory"

 

- Creates `/home/ubuntu/king` directory with `755` permissions.   

---

### 4️⃣ Install OpenJDK

ansible servers -i inventory -m ansible.builtin.apt
-a "name=openjdk-17-jdk state=present"

 

- Installs `openjdk-17-jdk` on all hosts in `servers`.   

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
Playbook → repeatable, structured automation.   
