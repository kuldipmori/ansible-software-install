# Ansible Installation and Software Deployment Guide

📚 Overview

This README file provides step-by-step instructions on how to install Ansible on a local Linux machine and use it to manage software installations. Ansible is a powerful automation tool that simplifies the process of managing configurations and deploying applications across multiple servers.

🛠️ Prerequisites

Before you begin, ensure that you have the following 📝:

1. A local Linux machine (e.g., Ubuntu, CentOS . . .) with root or sudo access.
2. Internet connectivity to download Ansible and software packages.
3. Basic knowledge of the Linux command line.

## 🚀 Install Ansible on Linux, follow these steps:

1. Add the Ansible repository to your system's package manager:
```
sudo apt-add-repository ppa:ansible/ansible
```

2. Update the package lists to include the newly added repository:
```
sudo apt update
```

3. Install Ansible:
```
sudo apt install ansible
```

4. Verify the Ansible installation by checking the version:
```
ansible --version
```

The output should display the installed Ansible version information, confirming that the installation was successful.

## 🔧 Setup Ansible-Hosts file
The `/etc/ansible/hosts` file is the inventory file used by Ansible to define and organize the hosts (remote servers) that Ansible will manage. It is a text file that lists the hostnames or IP addresses of the remote servers and organizes them into groups.

For external machine or server,

```[target-server] = Your target server name.```

```Replace 13.200.130.21 with your target server IP(s).```

```
sudo nano /etc/ansible/hosts
```

```
#Ansible-Target-Server
[target-server]
13.200.130.21
``` 

For local machine or system,
```
sudo nano /etc/ansible/hosts
```


```
#Localhost
[localhost]
127.0.0.1 ansible_connection=local
``` 

## 📂 Code Clone 

1. Code clone on Local Machine.
```
git clone https://github.com/anchor-it/ansible-software-install.git
```

2. Enter in Direcotry.
```
cd ansible-software-install
```

3. Excute Playbook
```
sudo ansible-playbook *.yaml
```

## 📂 Code Directories
```
.
├── cache-service
│   └── redis-install.yaml
├── package-management
│   └── apt-manage.yaml
├── README.md
├── software-install
│   ├── chrome-install.yaml
│   └── vscode-install.yaml
└── web-server
    └── nginx-install.yaml

4 directories, 6 files
```

Playbook file permission 
```
-rwxr-xr-x  1 USER USER  312 Jul 18 11:03 *.yaml*
```

For Excute playbooks in Linux-machine 
```
sudo ansible-playbook *.yaml
```

## 📋 Playbook Descriptions

⚠️ NOTE: Make sure to run the playbook with appropriate privileges (e.g., sudo) to perform package management operations.

1. ```package-management```: This directory contains the apt-manage.yaml playbook, which handles package management tasks specific to the system's package manager (APT in this case). It may include tasks like updating the package cache, upgrading packages, or removing packages.

2. ```software-install```: This directory contains the chrome-install.yaml and vscode-install.yaml playbooks. These playbooks handle the installation and configuration of specific software packages, such as Google Chrome and Visual Studio Code.

3. ```web-server```: This directory includes the nginx-install.yaml playbook. It focuses on the installation and setup of a web server, specifically Nginx, including tasks like package installation, configuration, and service management.

4. ```cache-service```: Automated Redis cache server installation with Ansible. Easily set up Redis server and CLI on target servers using the redis-install.yaml playbook. 

🎉 Enjoy your automated Linux software deployments! 🍕
