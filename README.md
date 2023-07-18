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

sudo nano /etc/ansible/hosts

```
#Ansible-Target-Server
[target-server]
13.200.130.21
``` 

For local machine or system,

sudo nano /etc/ansible/hosts

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
ansible-playbook *.yaml
```

Playbook file permission 
```
-rwxr-xr-x  1 USER USER  312 Jul 18 11:03 apt-manage.yaml*
-rwxr-xr-x  1 USER USER  500 Jul 18 10:41 chrome-install.yaml*
-rwxr-xr-x  1 USER USER  531 Jul 18 11:18 vscode-install.yaml*
```

For Excute playbooks in Linux-machine 
```
sudo ansible-playbook *.yaml
```

## 📋 Playbook Descriptions

⚠️ NOTE: Make sure to run the playbook with appropriate privileges (e.g., sudo) to perform package management operations.

```[ For manage update pacakge ] apt-manage.yaml```
- Update apt cache: Updates the local package cache to ensure the latest package information is available.

- Upgrade packages: Upgrades all installed packages to the latest available versions. This ensures your system has the latest security patches and feature updates.

- Autoremove unused packages: Removes any packages that are no longer required by the system. This helps free up disk space and keeps the system clean.


```[ For isntall chrome-browser ] chrome-install.yaml```
- Add Google Chrome repository key: Downloads and adds the Google Chrome repository key to the system's keyring. This key is necessary for package verification.

- Add Google Chrome APT repository: Adds the Google Chrome APT repository to the system's list of software sources. This repository provides access to the Google Chrome packages.

- Install Google Chrome: Uses the apt module to install the google-chrome-stable package. This package contains the latest stable version of Google Chrome.

```[ For install vs-code ] vscode-install.yaml```

- Add Microsoft GPG key: Downloads and adds the Microsoft GPG key to the system's keyring. This key is required to authenticate the Visual Studio Code repository.

- Add VS Code repository: Adds the Visual Studio Code APT repository to the system's list of software sources. This repository provides access to the Visual Studio Code packages.

- Install VS Code: Uses the apt module to install the code package, which contains Visual Studio Code.

🎉 Enjoy your automated Linux software deployments! 🍕
