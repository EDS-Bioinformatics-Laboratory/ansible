# Ansible

Repository for installation of frequently used software on empty virtual machines.

Developed by:

* Barbera van Schaik, b.d.vanschaik@amsterdamumc.nl
* Antoine van Kampen, a.h.vankampen@amsterdamumc.nl
* Perry Moerland, p.d.moerland@amsterdamumc.nl



**NOTE: the scripts in the root folder are obsolete.**



## Documentation

See Barbera's [slide deck](https://github.com/EDS-Bioinformatics-Laboratory/BioLabMatters/blob/master/Presentations/Schaik_20251016-tutorial-VM-ansible.pptx) for examples of how to make this work on MyDre and SURF.

## Requirements

The Ansible script assumes a virtual machine running Ubuntu. It might also work on Debian.

## Setting up an Ubuntu VM

1. Create a new VM on myDre

2. Login to the VM using your myDRE account using RDP (X environment, or SSH  (terminal).

```
sudo apt update
sudo apt upgrade 
```

3. Stop and restart the VM, and login again.

4. Install Ansible and Git.

```
sudo apt install software-properties-common
sudo apt install ansible git
```


5. Clone the ansible repository

```
git clone https://github.com/EDS-Bioinformatics-Laboratory/ansible.git
cd ansible
```

Configure ``config.yml``: change the username to your own username.

## Installation and configuration of software with Ansible

Run a sudo command before you run ansible, otherwise the script can't do operations as root

```
sudo ls
```

Execute playbooks

```
ansible-playbook -i hosts -v General.yml
```

Disconnect from the VM and start a new session, this will:

- Activate conda by sourcing the bashrc
- Enable visual output via X11 (e.g. for VScode)

VScode can run from the commandline: ``code &``

## Software installation

* python
* conda
* VScode
* Apptainer (Singularity)
* R, renv

## To implement

* common libraries via renv
* common python packages via conda environment
