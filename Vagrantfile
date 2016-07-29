# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  #----------------------
  # Global configuration
  #----------------------
  config.vm.synced_folder "./sync", "/vagrant_data"
  config.vm.provision "shell", inline: 'cat /vagrant_data/devlab1_rsa.pub >> /home/vagrant/.ssh/authorized_keys'
  config.vm.box = "ubuntu/trusty64"

  #-------------------------
  #        Jenkins 2
  #-------------------------
  config.vm.define "jenkins2" do |machine|
    machine.vm.hostname = "devlab1-jnks001v"
    machine.vm.network "private_network", ip: "192.168.10.10"
    machine.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    machine.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook_jenkins.yml"
    end
  end

  #-------------------------
  #        Gitlab
  #-------------------------
  config.vm.define "gitlab" do |machine|
    machine.vm.hostname = "devlab1-glab001v"
    machine.vm.network "private_network", ip: "192.168.10.11"
    machine.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    machine.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook_gitlab.yml"
    end
  end

  #-------------------------
  #        Nexus
  #-------------------------
  config.vm.define "nexus" do |machine|
    machine.vm.hostname = "devlab1-nexs001v"
    machine.vm.network "private_network", ip: "192.168.10.12"
    machine.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    machine.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook_nexus.yml"
    end
  end

end
