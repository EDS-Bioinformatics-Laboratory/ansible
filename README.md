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

## Install basics

Update the git repository

```
cd ansible
git pull origin main
```

Install general software

```
ansible-playbook -i hosts -v general-VM.yml
```
