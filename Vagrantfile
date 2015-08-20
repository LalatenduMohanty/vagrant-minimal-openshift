# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"

  config.vm.provider "virtualbox" do |vbox, override|
    vbox.cpus = 2
    vbox.memory = 1024
    vbox.customize ["modifyvm", :id, "--ioapic", "on"]
  end
  config.vm.provider "libvirt" do |libvirt, override|
    libvirt.cpus = 2
    libvirt.memory = 1024
    libvirt.driver = 'kvm'
  end

  config.vm.provision "shell", inline: <<-SHELL
     sudo yum update
     sudo yum install openshift
  SHELL
end
