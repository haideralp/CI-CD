# Ansible - Configuration Management ?

## Diagram Display of Ansible Configuration In Hybrid Setting

![image](https://user-images.githubusercontent.com/97620055/188432069-1eca356a-9bc1-41c2-9fcc-0b707825a4ff.png)


## What is Ansible ?
- A powerful automation tool used to con

## Benefits of Ansible


## Running of Multiples VMs: Controller, Web (Agent), Database (Agent)
  
- Using the vagrant file in IAC repository I spun up three virtual machines that are defined as a controller, web and database as per the diagram shown. 
- Start Vms: `vagrant up` then check it was successfull with `vagrant status`, if not do so individually. 
- Ensure three distinguish IP addresses are allocated for them. Controller: `192.168.33.12`, Web:`192.168.33.10`, DB:`192.168.33.11`
- Check for internet connection on nodes using, `ping ip address of vm` individually.
- Ensure `sudo apt update/upgrade -y` are run on the agent nodes as well as controller.
  

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
  
## Setting up SSH connection from controller to nodes:

- Running `sudo ansible nodename -m ping` will give error due to security reasons so this was then configured in hosts file located in default `cd /etc/ansible/`.
- Enter hosts file with `sudo nano hosts` once in the default location. 
- Specify the settings as follows:
    


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