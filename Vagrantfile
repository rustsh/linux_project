# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.define "db1" do |db1|
    db1.vm.hostname = "db1"
    db1.vm.network "private_network", ip: "10.10.10.20"
    db1.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/db1.yml"
    end
  end

  config.vm.define "web1" do |web1|
    web1.vm.hostname = "web1"
    web1.vm.network "private_network", ip: "10.10.10.11"
    # web1.vm.provider "virtualbox" do |vb|
    #   vb.memory = 1024
    #   vb.cpus = 2
    # end
    web1.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/web1.yml"
    end
  end

  config.vm.define "web2" do |web2|
    web2.vm.hostname = "web2"
    web2.vm.network "private_network", ip: "10.10.10.12"
    web2.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/web2.yml"
    end
  end

  config.vm.define "web3" do |web3|
    web3.vm.hostname = "web3"
    web3.vm.network "private_network", ip: "10.10.10.13"
    web3.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/web2.yml"
    end
  end

end
