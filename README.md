# DevOps10

This vagrant will install 3 Ubuntu 18.04 machines, 2x Nginx webserver and 1 ubuntu server for Nginx loadbalancing.
It will add some default users, groups and directory's. By default 3 webservers with no content.
This Vagrant is to practice with Loadbalancing.
This repository is intended for educational purpose only.


## Prerequisites

Works on Windows 10 and tested on macOS (macOS needs the Virtualbox extension pack).

Software needed:
* Virtualbox 5.0 or higher
* Git bash for Windows
* Vagrant 2.2.6 or higher


## Demo installation && use Vagrant

Youtube: https://youtu.be/KABnIuaA8SM


## Demo loadbalancing with Nginx

Youtube: 


## Installation

* Install Virtualbox: https://www.virtualbox.org/wiki/Downloads
* Install Git bash for Windows: https://gitforwindows.org/
* Install Vagrant for Windows: https://www.vagrantup.com/downloads.html

## Run this Vagrant VM
Open **Git Bash** in Windows
```
cd Documents
mkdir vagrant && cd vagrant
git clone https://github.com/borahuho/DevOps10
cd DevOps10
vagrant up
vagrant ssh lb01
```
## Mission

Read your mission in "Opdracht"

## Network
Vagrant VM will be set up with 2 network adapters
```
Nat : DHCP
Localhost (lb01): 192.168.10.130

Nat : DHCP
Localhost (web01): 192.168.10.135

Nat : DHCP
Localhost (web02): 192.168.10.136
```
## Vagrant commands
Start VM's with Vagrant
```
vagrant up
```
Pause a VM
```
vagrant suspend
```
Restart a paused VM
```
vagrant resume
```
Stop and shutdown a VM
```
vagrant halt
```
Remove a VM
```
vagrant destroy
```
ssh in to the VM
```
vagrant ssh lb01
vagrant ssh web01
vagrant ssh web02
```

