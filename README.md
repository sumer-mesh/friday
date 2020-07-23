## Friday

> Many of people all want to jump into the Cloud Native industry and whatever it cost and where it comes from(architecture transformation ), and just focus on Kubernetes, but no one wants to ask how to set up the initialization environment quickly. Especially in the small or medium team or company, that stupid.


## Quick Start

```
#
# Create the new machine with Ubuntu
# vagrant up 
#
# Downloading the environment and use remote container development loginto the container to run the ansible script
docker pull aisuko/ansible:v0.1.0
#
# Running all the tasks
ansible-playbook deploy.yml -i hosts
# 
# The single script
ansible -i hosts all -m shell -a "date"
#
# SSH into the vagrant
#
# vagrant ssh-config --host default
#
# Do not set the static IP(May not work in the `aisuko/ansible:v0.1.0` container)
ssh vagrant@localhost -p 2222 -i .vagrant/machines/default/virtualbox/private_key
#
# Set the static IP
ssh vagrant@192.168.33.10 -i /root/code/friday/.vagrant/machines/default/virtualbox/private_key



#
# Example
➜  friday git:(master) ✗ ssh vagrant@192.168.33.10 -i /root/code/friday/.vagrant/machines/default/virtualbox/private_key        
Welcome to Ubuntu 14.04.6 LTS (GNU/Linux 3.13.0-170-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Thu Jul 23 03:37:36 UTC 2020

  System load:  0.0               Processes:           74
  Usage of /:   3.6% of 39.34GB   Users logged in:     0
  Memory usage: 25%               IP address for eth0: 10.0.2.15
  Swap usage:   0%                IP address for eth1: 192.168.33.10

  Graph this data and manage this system at:
    https://landscape.canonical.com/

UA Infrastructure Extended Security Maintenance (ESM) is not enabled.

0 updates can be installed immediately.
0 of these updates are security updates.

Enable UA Infrastructure ESM to receive 64 additional security updates.
See https://ubuntu.com/advantage or run: sudo ua status


Last login: Thu Jul 23 03:37:36 2020 from 10.0.2.2
vagrant@vagrant-ubuntu-trusty-64:~$ exit
logout
Connection to 192.168.33.10 closed.




#
# Example for executing the ansible command in the ansible container
root@c5ecdf5aae24:/workspace# ansible -i hosts all -m shell -a "date"
192.168.33.10 | CHANGED | rc=0 >>
Thu Jul 23 06:40:22 UTC 2020
```