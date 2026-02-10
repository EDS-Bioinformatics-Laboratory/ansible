# Ansible

Repository for installation of frequently used software on empty virtual machines.

Developed by:

* Barbera van Schaik, b.d.vanschaik@amsterdamumc.nl
* Antoine van Kampen, a.h.vankampen@amsterdamumc.nl
* Perry Moerland, p.d.moerland@amsterdamumc.nl



**NOTE: the scripts in the root folder are obsolete.**



## Requirements

The Ansible script assumes a virtual machine running Ubuntu. It might also work on Debian.

## Manual steps

Login to the VM and install Ansible and Git.

```
sudo apt update
sudo apt install software-properties-common
sudo apt install ansible git
```

Clone this repository

```
git clone https://github.com/EDS-Bioinformatics-Laboratory/ansible.git
```

Configure ``config.yml``: change the username to your own username.

## Installation with Ansible

Run a sudo command before you run ansible, otherwise the script can't do operations as root

```
sudo ls
```

Install software

```
ansible-playbook -i hosts -v general-VM.yml
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
