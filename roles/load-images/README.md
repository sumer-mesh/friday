# docker-images

Ansible role to load images onto a remote Docker host where access to a registry is not possible.


## Requirements

- Ansible >= 2.3

On Ansible control machine and host that executes module:

- `python` >= 2.6
- `docker-py` >= 1.7.0
- `Docker API` >= 1.20

## Role Variables

- `images`: List of image names and tags to pull from registries
- `tars`: List of tarballs to load

```
If you do not familiar with Ansible, please do not change other configurations which you do not know.

# We want to use passwd, because simple for you guys
sudo apt update -y && sudo apt-get install sshpass -y

# Check the host address
$ ansible --list-hosts all

# Check the host address
$ ansible -i remote-machines.txt --list-hosts all

# Check the worker
$ ansible --list-hosts worker

# Check the file
ansible -m command -a "ls" all

# run container and mount code 
docker run --name test-rc3 -it --sig-proxy=false -a STDOUT -a STDERR --mount source=/home/aisuko/Documents/vscode-dev-containers/containers/azure-ansible,target=/workspace,type=bind,consistency=delegated aisuko/ansible:2.10.8-rc1 /bin/bash

-------------------------------------------------------------------------------------
# Add your hosts to the configuration `remote-machines.txt` at the root folder

# Add your docker image tar and name to the `engine/fastdata-engine.yml`

# Execute load docker file to remote target
ansible-playbook engine/load-images-engine.yml

As you can see below that we load image to remote succeed.

root ➜ /workspace/docker-images (master ✗) $ ansible-playbook engine/fastdata-engine.yml
[WARNING]: Found both group and host with same name: master

PLAY [Load Images] ****************************************************************************************************************************************************************************

TASK [Gathering Facts] ************************************************************************************************************************************************************************
ok: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : include] ******************************************************************************************************************************************
included: /workspace/docker-images/tasks/tars.yml for 172.16.21.183 => (item=../tarballs/hello-world.tar)
included: /workspace/docker-images/tasks/tars.yml for 172.16.21.183 => (item=../tarballs/alpine.tar)
included: /workspace/docker-images/tasks/tars.yml for 172.16.21.183 => (item=../tarballs/busybox.tar)

TASK [/workspace/docker-images/engine/../ : Get temporary file on remote machine] *************************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Copy ../tarballs/hello-world.tar to remote host] **************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Load image on remote] *****************************************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Delete Temporary File on Remote] ******************************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Get temporary file on remote machine] *************************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Copy ../tarballs/alpine.tar to remote host] *******************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Load image on remote] *****************************************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Delete Temporary File on Remote] ******************************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Get temporary file on remote machine] *************************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Copy ../tarballs/busybox.tar to remote host] ******************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Load image on remote] *****************************************************************************************************************************
changed: [172.16.21.183]

TASK [/workspace/docker-images/engine/../ : Delete Temporary File on Remote] ******************************************************************************************************************
changed: [172.16.21.183]

PLAY RECAP ************************************************************************************************************************************************************************************
172.16.21.183              : ok=16   changed=12   unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```