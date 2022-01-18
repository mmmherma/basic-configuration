# basic-configuration

Machine basic configuration based on Debian XFCE.

## Update system

```bash
su - root
apt install sudo
usermod -aG sudo <user>
sudo reboot
```

## Install VirtualBox and Vagrant

Download [VirtualBox](https://www.virtualbox.org/wiki/Downloads) and [Vagrant](https://www.vagrantup.com/downloads) or type the following commands into a terminal:

```bash
su - root
su - <user>

# Install dependencies
sudo apt install wget

# Download software
cd Downloads/
wget https://download.virtualbox.org/virtualbox/6.1.32/virtualbox-6.1_6.1.32-149290~Debian~bullseye_amd64.deb
wget https://download.virtualbox.org/virtualbox/6.1.32/Oracle_VM_VirtualBox_Extension_Pack-6.1.32.vbox-extpack
wget https://releases.hashicorp.com/vagrant/2.2.19/vagrant_2.2.19_x86_64.deb

# Install software
# VirtualBox
sudo apt install dkms
sudo dpkg -i https://download.virtualbox.org/virtualbox/6.1.32/virtualbox-6.1_6.1.32-149290~Debian~bullseye_amd64.deb
sudo apt --fix-broken install
VBoxManage --version
sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-6.1.32.vbox-extpack
# Vagrant
sudo dpkg -i vagrant_2.2.19_x86_64.deb
vagrant --version
```

## Install Docker

Install [Docker](https://docs.docker.com/engine/install/debian/) using the official documentation or type the following commands into a terminal:

```bash
# Install Docker
sudo apt remove docker docker-engine docker.io containerd runc
sudo apt update
sudo apt install ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo usermod -aG docker <user>

# Install docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```
