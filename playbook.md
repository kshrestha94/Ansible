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

# configure reverse proxy

  - name: Customize Nginx default configuration file
    lineinfile:
      path: /etc/nginx/sites-available/default
      regexp: '^(\s*try_files.*)$'
      line: '        proxy_pass http://localhost:3000;'

# restart nginx

  - name: Restart Nginx service
    service:
      name: nginx
      state: restarted




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
# which host to perform
- hosts: web

# see the log by gathering facts
# gathering_facts: yes

# admin access
  become: true

# install nodejs
  tasks:
  # add the instructions  -  install node 12 with pm2 and run the app
  - name: Installing node v 12the gog key for nodejs
    apt_key:
      url: "https://deb.nodesource.com/gpgkey/nodesource.gpg.key"
      state: present

  - name: Add NodeSource repository
    apt_repository:
      repo: "deb https://deb.nodesource.com/node_12.x {{ ansible_distribution_release }} main"
      state: present


  - name: Clone the Git repository
    git:
      repo: https://github.com/kshrestha94/tech241_sparta_app.git
      dest: /home/ubuntu/app

    become: yes

  - name: Install Node.js
    apt:
      name: nodejs
      state: present
      update_cache: yes

  - name: Install PM2
    npm:
      name: pm2
      global: yes
      state: present
      version: "4.5.6"


  - name: Install app dependencies
    command: npm install
    args:
      chdir: /home/ubuntu/app/app/


  - name: Start the Node.js app
    command: pm2 start app.js
    args:
      chdir: /home/ubuntu/app/app
```
# creating a playbook for database (mongodb)

![Alt text](<db ansible architecture.png>)

# create new playbook for mongodb db 
```
sudo nano mongodb-playbook.yml
```

```
---

# create a playbook to install mongodb in db-machine/instance

# who will be the host?

- hosts: db

# get the logs

  gather_facts: yes

# admin access
  become: true

# provide instructions - tasks

  tasks:

# intall mongodb

  - name: Installing Mongodb
    apt: pkg=mongodb state=present

# ensure the db in runnning

# check the status if it's running or not using adhoc commands

```
### run playbook
```
sudo ansible-playbook mongodb-playbook.yml
```
#### check if status is running 
```
sudo ansible db -a "systemctl status mongodb"
```