# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/8"

#  config.vm.provision "ansible" do |ansible|
#    ansible.verbose = "vvv"
#    ansible.playbook = "provisioning/playbook.yml"
#    ansible.sudo = "true"
#  end

  config.vm.provider "virtualbox" do |v|
	  v.memory = 256
  end

  config.vm.define "r1" do |r1|
    r1.vm.network "private_network", ip: "10.0.0.1", virtualbox__intnet: "r1r2"
    r1.vm.network "private_network", ip: "10.10.0.1", virtualbox__intnet: "r1r3"
    r1.vm.hostname = "r1"
  end

  config.vm.define "r2" do |r2|
    r2.vm.network "private_network", ip: "10.0.0.2", virtualbox__intnet: "r1r2"
    r2.vm.network "private_network", ip: "10.20.0.1", virtualbox__intnet: "r2r3"
    r2.vm.hostname = "r2"
  end

  config.vm.define "r3" do |r3|
    r3.vm.network "private_network", ip: "10.20.0.2", virtualbox__intnet: "r2r3"
    r3.vm.network "private_network", ip: "10.10.0.2", virtualbox__intnet: "r1r3"
    r3.vm.hostname = "r3"
  end
end
