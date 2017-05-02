# -*- mode: ruby -*-
# vi: set ft=ruby :

suffix="dev01"
fqdn="local"

Vagrant.configure("2") do |config|

  # User debian/contrig-jessie64 Template
  config.vm.box = "ubuntu/yakkety64"
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"

  config.vm.define "gui" do |gui|
    config.vm.provider "virtualbox" do |v|
      # Set hostname for vm
      config.vm.hostname = "#{suffix}-gui.#{fqdn}"
      # Set VM name
      v.name = "#{suffix}-gui.#{fqdn}"
      # Display the VirtualBox GUI when booting the machine
      v.gui = false
      # Customize the amount of memory on the VM:
      v.memory = "2048"
      # Enable 3D Acceleration
      v.customize ["modifyvm", :id, "--accelerate3d",  "on"]
      # Set Video Memory to 128MB
      v.customize ["modifyvm", :id, "--vram", "128"]
    end
    # Provision of Linux Gui with ansible
    config.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/main.yaml"
      ansible.verbose = false
    end
  end
end
