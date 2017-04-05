# Setup for various tech-related devices
A way to keep track of what's been done to set up various devices I've come in contact with

## Ubuntu Server - Samba File Server + CUPS Printer Sharing (5 Apr 2017)
### Used software:

| Software Name | Install Instructions |
| --- |--- |
| Ubuntu Server v16.10 | https://www.ubuntu.com/download/server
| Samba v4.4.5-Ubuntu | `sudo apt install samba smbfs & samba -V`
| SSH + OpenSSH Server | `sudo apt install ssh openssh-server`

| Reference Material |
| --- |
| [How to Set Up & Enable SSH on Ubuntu](https://www.maketecheasier.com/setup-enable-ssh-ubuntu/) |

### Steps taken:
1) Install Ubuntu Server v16.10 on hardware (make bootable USB with Startup Disk Creator, during install process use guided partitioning, install to 500GB drive less 4GB swap, `uname` and `pwd` are name of person who installed)
2) Install SSH and OpenSSH (see install instructions)
   > To change the SSH configuration, `sudo nano /etc/ssh/sshd_config` and edit the config file as necessary
3) Backup default SSH config file: `sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak` and `sudo chmod a-w /etc/ssh/sshd_config.`
4) Make `ssh` directory in home and change permissions: `mkdir ~/.ssh & chmod 700 ~/.ssh`
5) Generate ssh key: `ssh-keygen -t rsa` (blank password)
