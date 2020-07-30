# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.define "db1" do |db1|
    db1.vm.hostname = "db1"
    db1.vm.network "private_network", ip: "10.10.10.20"
    db1.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/db.yml"
    end
  end

  config.vm.define "redis1" do |redis1|
    redis1.vm.hostname = "redis1"
    redis1.vm.network "private_network", ip: "10.10.10.31"
    redis1.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/redis.yml"
    end
  end

  config.vm.define "nfs1" do |nfs1|
    nfs1.vm.hostname = "nfs1"
    nfs1.vm.network "private_network", ip: "10.10.10.51"
    nfs1.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/nfs.yml"
    end
  end

  config.vm.define "web1" do |web1|
    web1.vm.hostname = "web1"
    web1.vm.network "private_network", ip: "10.10.10.11"
    web1.vm.network "forwarded_port", guest: 8080, host: 8080
    web1.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
    web1.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/web-first.yml"
    end
  end

  config.vm.define "web2" do |web2|
    web2.vm.hostname = "web2"
    web2.vm.network "private_network", ip: "10.10.10.12"
    web2.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
    web2.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/web-replica.yml"
    end
  end

  config.vm.define "web3" do |web3|
    web3.vm.hostname = "web3"
    web3.vm.network "private_network", ip: "10.10.10.13"
    web3.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
    web3.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/web-replica.yml"
    end
  end

  config.vm.define "ha1" do |ha1|
    ha1.vm.hostname = "ha1"
    ha1.vm.network "private_network", ip: "10.10.10.41"
    ha1.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/haproxy.yml"
    end
  end

  config.vm.define "ha2" do |ha2|
    ha2.vm.hostname = "ha2"
    ha2.vm.network "private_network", ip: "10.10.10.42"
    ha2.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbooks/haproxy.yml"
    end
  end

end
