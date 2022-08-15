# tfe-vagrant

This repository is creating a VM with Vagrant to install TFE manually with Self-Signed Certificate

### Prerequisites

- [X] [Terraform](https://www.terraform.io/downloads)
- [X] [Replicated license](https://hashicorp.atlassian.net/wiki/spaces/tfsupport/pages/676792039/Terraform+Enterprise+Installation#Replicated-license)
- [X]  [Vagrant](https://www.vagrantup.com/docs/installation)
- [X]  [VirtualBox](https://www.virtualbox.org/)

## How to Use this Repo

- Clone this repository:
```shell
git clone git@github.com:dlavric/tfe-vagrant.git
```

- Go to the directory where the repo is stored:
```shell
cd tfe-vagrant
```

- Start Vagrant
```shell
vagrant up
```

- Connect to the VM
```shell
vagrant ssh tfe
```

- Install TFE (for specific version follow this [KB](https://support.hashicorp.com/hc/en-us/articles/1500009010521-How-to-Install-Terraform-Enterprise-to-a-Specific-Version))
```shell
sudo curl -o /tmp/install.sh https://install.terraform.io/ptfe/stable

sudo chmod +x /tmp/install.sh

sudo /tmp/install.sh
```

- Follow the installation script prompts. Example output is below
```shell
Determining local address
The installer was unable to automatically detect the private IP address of this machine.
Please choose one of the following network interfaces:
[0] eth0        10.0.2.15
[1] eth1        192.168.56.51
Enter desired number (0-1): 0
The installer will use network interface 'eth0' (with IP address '10.0.2.15').
Determining service address
The installer was unable to automatically detect the service IP address of this machine.
Please enter the address or leave blank for unspecified.
Service IP address: 192.168.56.51
Does this machine require a proxy to access the Internet? (y/N) N
Installing docker version 20.10.7 from https://get.replicated.com/docker-install.sh


To continue the installation, visit the following URL in your browser:

  http://192.168.56.51:8800
```

- Configure TFE by following the steps from [here](https://hashicorp.atlassian.net/wiki/spaces/tfsupport/pages/676792039/Terraform+Enterprise+Installation#Replicated-console-access) 
```
Hostname: 192.168.56.51.nip.io

Choose `Self-Signed certificate` when asked to provide the custom SSL certificate on the screen.

Mounted Disk Path (Required) set to /mnt/tfe
```

- TFE is installed successfully

![TFE Dashboard](https://github.com/dlavric/tfe-vagrant/blob/main/pictures/Screenshot1.png)

- Uninstall TFE
```shell
curl https://install.terraform.io/tfe/uninstall > uninstall.sh

chmod +x uninstall.sh

sudo bash uninstall.sh

This script will completely uninstall Terraform Enterprise and Replicated on this system, as well as remove associated files.
Do you wish to continue? (y/n)yes
Proceeding with uninstall...
Stopping and disabling the replicated services...
....
....
Uninstall Complete

If you ran into any unexpected errors, please contact support@hashicorp.com
or visit the following url:
https://support.hashicorp.com/hc/en-us/articles/360043134793-Uninstalling-Terraform-Enterprise
```
