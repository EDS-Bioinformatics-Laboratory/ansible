# Setup default myDre VM 

Repository for installation of frequently used software on empty virtual machines (VM) on myDRE. This might also work on SURF Research Cloud but has not been tested yet.

Developed by:

* Barbera van Schaik, b.d.vanschaik@amsterdamumc.nl
* Antoine van Kampen, a.h.vankampen@amsterdamumc.nl
* Perry Moerland, p.d.moerland@amsterdamumc.nl



## Documentation

See Barbera's [slide deck](https://github.com/EDS-Bioinformatics-Laboratory/BioLabMatters/blob/master/Presentations/Schaik_20251016-tutorial-VM-ansible.pptx) for examples of how to make this work on MyDre and SURF.

## Requirements

The Ansible script assumes a virtual machine running Ubuntu. It might also work on Debian.

## Setting up an Ubuntu VM

* Create a new VM on myDre

* Login to the VM using your myDRE account using RDP (X environment, or SSH  (terminal).

```
sudo apt update
sudo apt upgrade 
```

* Stop and restart the VM, and login again.

* Install Ansible and Git.

```
sudo apt install software-properties-common
sudo apt install ansible git
```

* Clone the ansible repository

```
git clone https://github.com/EDS-Bioinformatics-Laboratory/ansible.git
cd ansible
```

* Modify the configuration file ``config.yml``: e.g., change the username to your own myDre username.



## Installation and configuration of software with Ansible

* Run a sudo command before you run ansible, otherwise the script can't do operations as root

```
sudo ls
```

* Execute playbooks

```
ansible-playbook -i hosts -v General.yml
```

General.yml will also create ~/Desktop/RD to which you can mount your Research Drive account (see below)

```
ansible-playbook -i hosts -v Vscode.yml
ansible-playbook -i hosts -v Conda.yml
source ~/.bashrc
```

This will activata conda.

VScode can run from the commandline: ``code &``

```
ansible-playbook -i hosts -v Bashrc.yml
ansible-playbook -i hosts -v Compilers.yml
ansible-playbook -i hosts -v R.yml
ansible-playbook -i hosts -v Julia.yml
ansible-playbook -i hosts -v Xemacs.yml
```

## Mount (SURF) Research Drive

Make sure you have a Research Drive account.

Use **Rclone** to mount Research Drive. Rclone is installed by one of the ansible playbooks above. Rclone is a command-line program to manage files on cloud storage. This makes it much easier to transfer files between your local computer and myDre in comparison to the default upload/download system.


If needed, then first install Rclone manually:

```
sudo -v ; curl https://rclone.org/install.sh | sudo bash
or
sudo apt install rclone
```

_Connect to your Research Drive account_ 
See: [SURF Wiki](https://servicedesk.surf.nl/wiki/spaces/WIKI/pages/117179081/RD+How+to+use+Rclone+with+Research+Drive) for more information to mount your Research drive

_Webdav URL (example):_ 
https://amsterdamumc.data.surf.nl/remote.php/dav/files/a.h.vankampen@amsterdamumc.nl

_Configuration is stored in:_
.config/rclone

_Example commands_
```
rclone ls RD:
rclone copy /my/folder RD:my/destination/folder
```

_Working with large objects_
When you want to upload large files to Research Drive, we recommend using a timeout of 10 minutes per gigabyte of the largest source file.

As an example, the largest file in the source directory is 5GB. Calculating the argument for --timeout gives: 10 minutes x 5GB = 50 minutes:

`rclone copy --use-cookies --timeout 50m ~/my_5gb_file.bin RD:my/destination/folder`

Important: Since this can cause data loss, test first with the --dry-run flag to see exactly what would be copied and deleted.
Note that files in the destination won’t be deleted if there were any errors at any point.
If my/destination/folder doesn’t exist, it is created and the contents of /my/folder goes there.


_Use Rclone to mount file systems in user space_
Using Rclone to mount a file system in user space is done as follows:

`rclone mount --use-cookies --timeout 15m RD: /path/to/local/mount`

The flag `--use-cookies` is needed, to get you always on the same Research Drive back-end, to prevent file lock between back-ends. The timeout flag is useful for uploading large files, we recommend using a timeout of 10 minutes per gigabyte of the largest source file.

You can unmount this file system by:

`fusermount -u /path/to/local/mount`
	
**Note:** the ansible playbook bashrc will add rdmount and rdumount to .bashrc



## **External Access list**

[[here](https://mydre.org/workspaces/dws-3049-AUBioLab/access/domain)]

The following websites should be added to the myDre [External Access List](https://support.mydre.org/portal/en/kb/articles/testing-self-service-domain-allowlisting) if these are not there already. This ensures that myDre can access these sites. The External Access List is global for all Workspaces and VMs. In principle, this list will never be deleted and, therefore, only needs to be setup once. In case you need access to another website (e.g., to install an R package), then simply add it to the list.

I also provide the list here in case is magically disappears on myDre. Then just copy this list back into the External Access List..

code.visualstudio.com  
office.com  
microsoftonline.com  
mydre.org  
conda.io  
anaconda.com  
anaconda.org  
amsterdamumc.data.surf  
julialang-s3.julialang.org  
google.nl  
google.com  
surf.nl  
rclone.org  
ubuntu.com  
github.com  
githubassets.com  
git-scm.com  
githubusercontent.com  
gitlab.com  
packages.microsoft.com  
conda-forge.org  
