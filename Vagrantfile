# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false
  config.vm.network "forwarded_port", guest: 5000, host: 80
  config.vm.network "forwarded_port", guest: 22, host:2222
  config.vm.provider "virtualbox" do |vb|
         vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
  end
  config.vm.provision "ansible" do |ansible|
         ansible.inventory_path = "hosts"
         ansible.playbook = "ansible_playbook.yml"
         ansible.limit = "all"
         ansible.sudo = true
  end   
end
