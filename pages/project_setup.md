---
permalink: project-setup
---

# Project Setup

## Virtualbox setup

If you do not have Virtualbox already installed on your machine, grab the executable for your platform by visiting the link below:

[Virtualbox Installer](https://www.virtualbox.org/wiki/Downloads)

Instructions for how to install Virtualbox on different platforms can be found here:

[Virtualbox Installation Details](https://www.virtualbox.org/manual/ch02.html)

Finally, make sure you install the **Virtualbox Extension Pack** which you can find on the same page where you obtained the Virtualbox Installer.

## Download appliances

You will need the following virtual appliances for this project. Details on how to use them are given in the next section.

[rocky_linux_base.ova](https://bcit365-my.sharepoint.com/:u:/g/personal/yshema_bcit_ca/EZrscfRAfoFAljRE76-u_PwB7dtfB-qkoOyWZAd5YM_OUw?e=bdU0Rt)

[border_rtr.ova](https://bcit365-my.sharepoint.com/:u:/g/personal/yshema_bcit_ca/EbSI06Ik3kJBh4rLHQW14zsBzBNddWF0ssYWQm960GMAEA?e=1e30Rm)

The _border router_ (`border_rtr`) provides some custom services which are needed for the project but cannot be configured directly on Virtualbox in-built NAT router

Rocky Linux is Red Hat-compatible Linux distribution with the same networking capabilities provided by Red Hat Enterprise servers. The `rocky_linux_base.ova` will be used as the base image for all other virtual devices that we will create for this project.

## Create your first network

### Your first network

In this activity, we are going to create two virtual machines, **r1** and **r2**, and connect them to a network which they will share with the host, i.e they will be directly accessible from the host.

Later, we will configure these two VM's to perform a variety of functions of which routing will be the most important.

All the VM's in this project use the same login credentials:

* Username: **admin**
* Password: **P@ssw0rd**

1. Launch Virtualbox
2. Create a host-only network (**Virtualbox Host-Only Ethernet Adapter #2** on Windows or **vboxnet2** if you are on Mac) with the following configuration:
   - IP Address: **10.26.20.253**
   - Subnet Mask: **255.255.255.0**
3. Import into Virtualbox the two appliances you downloaded earlier:
   * `border_rtr.ova`:
     - Name it **border_rtr**
     - Make sure its network adapters are configured as follows (this should already be the case except if you are on a Mac):
     - <ins>Adapter</ins> 1: Attached to **NAT**, adapter type (Paravirtualized), promiscuous mode (Allow all)
     - <ins>Adapter 2</ins>: Attached to **Virtualbox Host-Only Ethernet Adapter #2** (**vboxnet2** if you are on a Mac), adapter type (Paravirtualized), promiscuous mode (Allow all)
   * `rocky_linux_base.ova`: No need to do anything. We will use it only to clone other VM's (see next step)
     * Never run this image directly. If you do it can potentially interfere with any running VM that was cloned based off it.
4. Use the **rocky_linux_base.ova** image to clone two virtual machines and configure them as follows:
   - VM 1:
     - Name: **r1**
     - <ins>Adapter 1</ins>: Attached to **Virtualbox Host-Only Ethernet Adapter #2**, adapter type (Paravirtualized), promiscuous mode (Allow all), MAC address: **020000000001**
   - VM 2:
     - Name: **r2**
     - <ins>Adapter 1</ins>: Attached to **Virtualbox Host-Only Ethernet Adapter #2**, adapter type (Paravirtualized), promiscuous mode (Allow all), MAC address: **020000000002**

Start the VM's, making sure to start `border_rtr` first. Once all VM's are running, log into each and change the hostname to match the VM's name:

```
sudo hostnamectl set-hostname [vm_name]
```

You should now be able to send ping probes between the VM's or between the VM's and the outside networks.

## SSH setup

SSH (Secure Shell) is a software utility that allows you to securely log into a running system remotely. By default, SSH will prompt you for the remote host's hostname (or IP address), username and password, but it is possible to enable password-less login using public key/private key pair.

The **rocky_linux_base.ova** is already configured with a public key, so all we need is a private key which you can download from here:

[acit_admin_id_rsa](https://bcit365-my.sharepoint.com/:u:/g/personal/yshema_bcit_ca/EV4oSICRu9FPrCKMKrdHoa4BAG_z8kFvz1SoYZzBuST8Qw?e=TFv7WA)

Next, complete the following steps:

1. Locate the .ssh folder under your host's home directory and copy the key you just downloaded into this folder
2. Create a text file called `config` inside this `.ssh` folder and add content similar to the following:

```
host border
    Hostname 10.26.20.254
    User admin
    IdentityFile ~/.ssh/acit_admin_id_rsa

host r1
    Hostname 10.26.20.100
    User admin
    IdentityFile ~/.ssh/acit_admin_id_rsa

host r2
    Hostname 10.26.20.200
    User admin
    IdentityFile ~/.ssh/acit_admin_id_rsa
```

From your host's command-line interface (e.g. Powershell), try and access one of your VM's via SSH:
e.g. `ssh r1`