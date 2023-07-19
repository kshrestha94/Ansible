# Playbook and AD hoc commands

`why use adhoc commands?` 

check os of all nodes without habing to SSH into each manually 

cd /etc/ansible
sudo apt install tree -y
sudo nano hosts (change ip address of webb and db) 

sudo ansible web -a "sudo apt update -y"
sudo ansible db - a "sudo apt update -y"

sudo ansible web -m ping
sudo ansible db -m ping

### check version 
```
sudo ansible web -a "uname -a"
```

### check region
```
sudo ansible web -a "date"
```

### how much space available and free
```
sudo ansible web -a "free"
```

### folders
```
sudo ansible web -a "ls -a"
```
### create and edit file
```
sudo nano test.text
```

### show whats in the file
```
cat test.text
```
### check host file 
```
ls -a
```

### copy file from host to web
```
sudo ansible web -m copy -a "src=/etc/ansible/test.text dest=/home/ubuntu/test.text"
```

### check folder
```
sudo ansible web -a "ls -a"
```

### copy test.text file from home to web
```
sudo ansible web -m copy -a "src=/etc/ansible/test.text dest=/home/ubuntu/test.text"
```

### check files in web home directory  to see if test.text file has copied
```
sudo ansible web -a "ls -a"
```
### present working directory 
```
pwd
```

### create nginx playbook and script in YML
```
sudo nano nginx-playbook.yml
```

```
# Why YAML? human readable
# YAML file with --- three dashes
# Why playbook - apply repetitive tasks
# create a playbook to install nginx in web node

---

# which host to perform the task
- hosts: web

# see the logs by gathering facts
  gather_facts: yes
# admin access (sudo)
  become: true
# add the instructions - install nginx - to web node
  tasks:
  - name: Installing Nginx
    apt: pkg=nginx state=present
# ensure status of nginx is actively running (systemctl)

# adhoc command to check the status

```

### display what is in playbook file
```
cat nginx-playbook.yml
```

### run playbook with root
```
sudo ansible-playbook nginx-playbook.yml
```

### run nginx status
```
sudo ansible web -a "systemctl status nginx"
```

`copy and paste public IP of web vm and nginx should load`


# creating playbook and install node.js

### create new playbook
```
sudo nano nodejs-playbook.yml
```

```
---

# Which host to perform the task
- hosts: web

# See the logs by gathering facts
  gather_facts: yes

# admin access is required.
  become: true

# add the instructions - install Nodejs - web
  tasks:

  - name: Update apt cache
    apt:
      update_cache: yes

  - name: Ugrade packages
    apt:
      upgrade: dist

  - name: Clone repository
    git:
      repo: https://github.com/kshrestha94/tech241_sparta_app.git
      dest: app


  - name: Installing Node.js
    apt:
      state=present


  - name: Installing npm
    shell: npm install
    args:
       chdir: /home/ubuntu/app/app
       warn: false

  - name: Npm start
    command: sudo npm start
    args:
       chdir: /home/ubuntu/app/app
```

`npm start will hang but if you go to your web vm public IP:3000 sparta app will load.`

# pending tasks

automate using pm2 

add reverse proxy 



