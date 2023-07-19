# Infrastructure as Code (IaC)
```
IAC stands for Infrastructure as Code, which is the practice of managing and provisioning computer infrastructure through machine-readable definition files, enabling automated and consistent deployment and management of resources.

codify (user stories) everything in particular langauge (YAML) 
immutable 
on prem, hybrid, and cloud (AWS)

```
`configureation management with ansible`   
```
cheff
set node (VM) and agent node 
- playbooks used to automate scripts to multiple vms simutaneously in YAML 

owned by redhat:
python based, agent less, SSH, free and open source, push model

ansible tool - config tool in devops and devsec

HOST: iventory control file 
```
`orchestraction - terraform` - cloud indpendent; scripts are 
```
reuseable saving time  

aws cloudformmation 
```
![Alt text](<ansible architecture.png>)

# creating ansible controller and agent nodes

```
create 3 EC2 instances (controller, webb, db)
SSH into your controller VM
```

# commands to run of controller node

### 1. `update package list using root access`
```
sudo apt update -y
```

### 2. `install software properties common utilities for managing software repositories and add personal package archive repositories`
```
sudo apt-get install software-properties-common
```
### 3. `add ansible repository (open source IT automation tool) and install onto your system`
```
sudo apt-add-repository ppa:ansible/ansible
```
### 4. `update packages`

```
sudo apt update -y
```
### 5. `install ansible`
```
sudo apt install ansible -y
```
### 6. `check for the correct version`
```
sudo ansible --version
```
### 7. `cd into your ansible folder to make configerations`
```
cd /etc/ansible
```
### 8. `cd into your ssh folder`

```
cd ~/.ssh
```
### 9. `ls to check what you have inside your ssh folder`

```
ls
```
### 10. `nano allows edit the file and add private key for tech241.pem`  
```
sudo nano tech241.pem
```
### 11. `give read access only to your tech241.pem file`
```
sudo chmod 400 tech241.pem
```
### 12. `check inside your folder`
```
ls
```
### 13. `SSH into your web app VM from the controller add sudo`
```
sudo ssh -i "****" ubuntu@ec2-63-33-68-63.eu-west-1.compute.amazonaws.com
```

### 14. `SSH into your db VM from the controller add sudo`
```
sudo ssh -i "***" ubuntu@ec2-3-253-195-197.eu-west-1.compute.amazonaws.com

```
### 15. `cd into ansible` 
```
cd /etc/ansible
```
### 16. `install tree package`
```
sudo apt install tree -y
```
### 17. `edit host file`
```
sudo nano hosts 
```
`add for both webb app and db`

```
[web]
ec2-instance ansible_host=<web pubic IP> ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/tech241.pem

[db]
ec2-instance ansible_host=<db pubic IP> ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/tech241.pem

```
### 18. `ping command to connect host in the web and db group to send test ping. If the hosts respond successfully, it indicates that the hosts are reachable and the connectivity is working fine. The command will display the output for each host, showing whether the ping was successful or not`
``` 
sudo ansible web -m ping
sudo ansible db -m ping
```
