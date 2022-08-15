# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "hashicorp/bionic64"

    config.vm.define "tfe" do |tfe|
        tfe.vm.hostname = "tfe"
        tfe.vm.network "private_network", ip: "192.168.56.51"
        tfe.vm.provider "virtualbox" do |v|     
            v.memory = 1024 * 4
            v.cpus = 2  
    end

    tfe.vm.provision "shell", path: "scripts/install_tfe.sh"
    
    end  


# Install Azure CLI and setup azure env variables

   # config.vm.provision "file", source: "scripts/azurerm.sh", destination: "/home/vagrant/azurerm.sh"
   # config.vm.provision "shell", inline: "cat /home/vagrant/azurerm.sh >> /home/vagrant/.bashrc"
   # config.vm.provision "shell", path: "scripts/install_azurecli.sh"
    
end