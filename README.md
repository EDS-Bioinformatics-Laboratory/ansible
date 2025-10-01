# Ansible
Barbera van Schaik, public repo for installation scripts virtual machines

## Manual steps

Install Ansible and Git

```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible # this line might give an error that you can ignore
sudo apt install ansible git
```

Clone this repository

```
git clone https://github.com/EDS-Bioinformatics-Laboratory/ansible.git
```

Configure ``general-VM.yml`` en ``config.yml``: change the username to your own username (at top of the scripts)

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
