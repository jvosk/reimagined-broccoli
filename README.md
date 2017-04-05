# Setup for various tech-related devices
A way to keep track of what's been done to set up various devices I've come in contact with

## Ubuntu Server - Samba File Server + CUPS Printer Sharing (5 Apr 2017)
### Used software:

| Software Name | Install Instructions |
| --- |--- |
| Ubuntu Server v16.10 | https://www.ubuntu.com/download/server |
| Samba v4.4.5-Ubuntu | `sudo apt install samba smbfs & samba -V` |
| SSH + OpenSSH Server | `sudo apt install ssh openssh-server` |
| `avahi-daemon` | `sudo apt install avahi-daemon` |

| Reference Material |
| --- |
| [How to Set Up & Enable SSH on Ubuntu](https://www.maketecheasier.com/setup-enable-ssh-ubuntu/) |

### Steps taken:
1) Install Ubuntu Server v16.10 on hardware (make bootable USB with Startup Disk Creator, during install process use guided partitioning, install to 500GB drive less 4GB swap, `uname` and `pwd` are name of person who installed)
2) Install SSH and OpenSSH (see install instructions)
   > To change the SSH configuration, `sudo nano /etc/ssh/sshd_config` and edit the config file as necessary
   >
   > Under Ubuntu v15.10 and up, `systemctl` handles daemons, so use `sudo systemctl restart ssh` or similar to start/stop/restart the `ssh` server
3) Backup default SSH config file: `sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak` and `sudo chmod a-w /etc/ssh/sshd_config.`
4) Make `ssh` directory in home and change permissions: `mkdir ~/.ssh & chmod 700 ~/.ssh`
5) Generate ssh key: `ssh-keygen -t rsa` (blank password)
   > #TODO: add instructions for SSH tunneling in with ssh key (currently unused)
6) Slight detour; to use `ssh` without knowing the server IP, we need to broadcast the hostname. `avahi-daemon` to the rescue! Install `avahi-daemon` on both SSH server and client (see instructions above) to broadcast hostnames. Check the server hostname with `host $HOSTNAME` (and, if needed, current user with `echo $USER`); this is the login info to use in the `ssh` command, with format `ssh [user]@[hostname]`
   > Note: If connecting to server via SSH from Windows, you'll need an SSH client, e.g. [PuTTy](http://www.chiark.greenend.org.uk/~sgtatham/putty/) or [MobaXterm](http://mobaxterm.mobatek.net/)
