# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.synced_folder "./shared", "/home/vagrant/shared"

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false

    # Customize the amount of memory on the VM:
    vb.name = "DST test ubuntu(xenial64)"
    vb.memory = "2048"
    vb.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt update
    apt install -y python-simplejson
  SHELL

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./provisioning/ansible/playbook.yml"
  end

end
