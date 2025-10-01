# Ansible
Barbera van Schaik, public repo for installation scripts virtual machines

## Start from scratch

Install Ansible

```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible # this line gives an error
sudo apt install ansible
```

Clone this repository

```
git clone https://github.com/EDS-Bioinformatics-Laboratory/ansible.git
```

Configure ``general-VM.yml`` en ``config.yml``: change the username to your own username.

## Install basics

Update the git repository

```
cd ansible
git pull origin main
```

Run a sudo command before you run ansible, otherwise the script can't do operations as root

```
sudo ls
```

Install general software

```
ansible-playbook -i hosts -v general-VM.yml
```

Disconnect from the VM and start a new session to:

- Activate conda by sourcing the bashrc
- Enable visual output via X11 (e.g. for VScode)

VScode can run from the commandline: ``code &``

## To implement

Install:

* ~~python~~
* ~~conda~~
* ~~VScode~~
* ~~Apptainer (Singularity)~~
* R, renv
* common libraries via renv
* common python packages via conda environment
