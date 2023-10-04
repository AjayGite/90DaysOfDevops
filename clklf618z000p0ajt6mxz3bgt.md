---
title: "Understanding Package Managers 
and "systemctl" in Linux"
datePublished: Thu Jul 27 2023 17:19:18 GMT+0000 (Coordinated Universal Time)
cuid: clklf618z000p0ajt6mxz3bgt
slug: understanding-package-managers-and-systemctl-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690468116231/1ba5f75e-e0f1-4862-9ae6-2a0574fb7fa9.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690478353015/c31009c8-8aa1-4cbf-94f8-829f897b0ee0.png
tags: linux, package-manager, systemctl, 90daysofdevops, trainwithshubham

---

### **Package Manager:**

A package manager is a software tool that automates the process of installing, updating, configuring, and removing software packages on a Linux distribution. It simplifies the software management process and handles dependencies, which are other software packages required for a particular application to work correctly.

### Common package managers in various Linux distributions are:

* **APT (Advanced Package Tool)**: Used in Debian and Debian-based distributions like Ubuntu.
    
* **DNF (Dandified YUM)**: Used in Fedora and Red Hat Enterprise Linux (RHEL) 8 and later versions.
    
* **YUM (Yellowdog Updater Modified)**: Used in RHEL 7 and earlier versions.
    
* **Pacman**: Used in Arch Linux and Arch-based distributions.
    

With a package manager, you can install new software packages, update existing ones to the latest versions, remove unnecessary packages, and search for available packages in the distribution's software repositories.

Let's explore some of the most commonly used package managers along with examples:

1. **APT (Advanced Package Tool) - Debian/Ubuntu:**
    
    * Install a package:
        
        ```bash
        sudo apt-get install package_name
        ```
        
    * Update package information (repository metadata):
        
        ```bash
        sudo apt-get update
        ```
        
    * Upgrade all installed packages:
        
        ```bash
        sudo apt-get upgrade
        ```
        
    * Remove a package:
        
        ```bash
        sudo apt-get remove package_name
        ```
        
2. **DNF (Dandified YUM) - Fedora/RHEL 8 and later:**
    
    * Install a package:
        
        ```bash
        sudo dnf install package_name\
        ```
        
    * Update all installed packages:
        
        ```bash
        sudo dnf update
        ```
        
    * Remove a package:
        
        ```bash
        sudo dnf remove package_name
        ```
        
3. **YUM (Yellowdog Updater Modified) - RHEL 7 and earlier:**
    
    * Install a package:
        
        ```bash
        sudo yum install package_name
        ```
        
    * Update all installed packages:
        
        ```bash
        sudo yum update
        ```
        
    * Remove a package:
        
        ```bash
        sudo yum remove package_name
        ```
        
4. **Pacman - Arch Linux:**
    
    * Install a package:
        
        ```bash
        sudo pacman -S package_name
        ```
        
    * Update all installed packages:
        
        ```bash
        sudo pacman -Syu
        ```
        
    * Remove a package:
        
        ```bash
        sudo pacman -R package_name
        ```
        

These package managers provide more than just basic installation and removal capabilities. They handle dependencies, automatically resolving and installing any required packages for the software you want to use. Additionally, you can search for packages, list installed packages, and perform many other package-related tasks with these tools.

### **You have to install Docker and Jenkins in your system from your terminal using package managers**

To install Docker and Jenkins on Ubuntu, you can use the `apt-get` package manager. Here are the steps:

Install Docker on Ubuntu:

```bash
ubuntu@ip-172-31-92-36:~$ sudo apt-get update -y
ubuntu@ip-172-31-92-36:~$ sudo apt-get install docker.io
```

Check if the docker service is up and running:

```bash
ubuntu@ip-172-31-92-36:~$ sudo service docker status
● docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2023-07-27 17:06:23 UTC; 15s ago
TriggeredBy: ● docker.socket
       Docs: https://docs.docker.com
   Main PID: 16758 (dockerd)
      Tasks: 7
     Memory: 28.8M
        CPU: 262ms
     CGroup: /system.slice/docker.service
             └─16758 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
```

Enable the service to start when the system reboots up:

```bash
ubuntu@ip-172-31-92-36:~$ sudo systemctl enable docker
```

Add your user to the "docker" group to avoid using "sudo" with Docker commands:

```bash
ubuntu@ip-172-31-92-36:~$ sudo usermod -aG docker ubuntu
ubuntu@ip-172-31-92-36:~$ cat /etc/group | grep -i ubuntu
ubuntu:x:1000:
docker:x:122:ubuntu
```

### **systemctl and systemd:**

Systemctl and systemd are essential components in modern Linux systems that play a crucial role in managing services and processes. Let's explore each of them:

`systemd` is a system and service manager for Linux operating systems. It is designed to replace the traditional SysV init system and brings several advantages, including faster boot times, parallel startup of services, and better management of system resources.  
`systemctl` is a command-line tool that interacts with the systemd service manager. It allows users to control and manage services, view their status, enable or disable them at boot, and more.

Common systemctl Commands:

* `systemctl start service_name`: Start a service.
    
* `systemctl stop service_name`: Stop a service.
    
* `systemctl restart service_name`: Restart a service.
    
* `systemctl enable service_name`: Enable a service to start automatically at boot.
    
* `systemctl disable service_name`: Disable a service from starting automatically at boot.
    
* `systemctl status service_name`: View the status of a service.
    
    **service:**
    
    * `service` is a legacy command that works with the older SysV init system, which was used by many Linux distributions before the widespread adoption of systemd.
        
    * While `service` can still be found on many systems, it is essentially a compatibility command for managing SysV-style init scripts.
        
    * `service` is simpler in functionality compared to `systemctl` and lacks some of the more advanced features provided by systemd