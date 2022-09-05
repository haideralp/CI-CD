# Ansible - Configuration Management ?

## Diagram Display of Ansible Configuration In Hybrid Setting

![image](https://user-images.githubusercontent.com/97620055/188432069-1eca356a-9bc1-41c2-9fcc-0b707825a4ff.png)


## What is Ansible ?
- A powerful automation tool used to con

## Benefits of Ansible


## Setting Up Ansible Controller 

- Ensure python 2.7 and above is installed. 
- Perform: `sudo apt update/upgrade -y` 
- Installed any missed software: `sudo apt-get install software-properties-common`
- Link ansible repository to local host: `sudo apt-add-repository ppa:ansible/ansible`
- Install ansible: `sudo apt-get install ansible -y`
- Check version of ansible: `ansible --version`
- Default ansible directory: `cd /etc/ansible/`
- Intstall tree for better visualisation of files and folders: `sudo apt install tree`

## Accessing Agent Nodes From Controller
  
- SSH into specified node (web/db) using: `ssh vagrant@ipofagentnode(app/db)`
- First time will ask you to confirm, type yes
- Specify password by typing > default password: `vagrant`
- Check for connection on nodes using: `ping ip address of node`
- 


Ansible Ping

Go into hosts specify ip, connection type, user name and password. 

sudo ansible web -m ping 

Recieved 'pong' status - 


default directoy - looked for entry- web - sends to rrequest to it is alive. Security checked. so we gave permission.
need to make sure end point are awake - can cannot to.
alwasy ssh from local host when debugging. otherwsie cannot from controller.

ansible all -a "uname -a"

ansible web -a "free"

ansible web/all -a "date" >> filename (to save into a file from console)

ansible web -m shell -a "uptime"

ansible web -m copy -a "src=/etc/ansible/test.txt dest=/home/vagrant"

playbooks - file .yml or .yaml  (yet ain't mark up language)

## Important Links For Ansible

* Documentation is rapid for ansbile ensure to check regulary for latest updates. 
  
- 