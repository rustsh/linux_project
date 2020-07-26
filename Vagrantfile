# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.define "db" do |db|
    db.vm.hostname = "dbserver"
    db.vm.network "private_network", ip: "10.10.10.20"
    db.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/postgresql.yml"
    end
  end

  config.vm.define "web" do |web|
    web.vm.hostname = "webserver"
    web.vm.network "private_network", ip: "10.10.10.10"
    web.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 2
    end
    web.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/nextcloud.yml"
    end
  end

end
