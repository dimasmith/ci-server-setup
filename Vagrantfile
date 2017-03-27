# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
  end

  config.vm.provision :ansible_local do |ansible|
    ansible.playbook = 'ansible/example.yml'
  end

  config.vm.network :private_network, ip: "192.168.1.10"

end
