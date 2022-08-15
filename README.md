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
The installer will use network interface 'ens5' (with IP address '192.168.56.51')
Determining service address
The installer will use service address '192.168.56.51' (discovered from EC2 metadata service)
The installer has automatically detected the service IP address of this machine as 192.168.56.51.
Do you want to:
[0] default: use 192.168.56.51
[1] enter new address
Enter desired number (0-1): 0
Does this machine require a proxy to access the Internet? (y/N) N
Installing docker version 18.09.2 from https://get.replicated.com/docker-install.sh
Once the installation completes, you’ll see output similar to the following.


To continue the installation, visit the following URL in your browser:

  http://192.168.56.51:8800
```

- Configure TFE by following the steps from [here](https://hashicorp.atlassian.net/wiki/spaces/tfsupport/pages/676792039/Terraform+Enterprise+Installation#Replicated-console-access) 
```
Hostname: 192.168.56.51.nip.io

Choose `Self-Signed certificate` when asked to provide the custom SSL certificate on the screen.
```

