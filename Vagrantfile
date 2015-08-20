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
     sudo yum -y update
     sudo cp sync/*.repo /etc/yum.repos.d/
     sudo yum -y install docker openshift-node openshift-master
     sudo systemctl enable docker openshift-master openshift-node
     sudo systemctl start openshift-master openshift-node
  SHELL
end
