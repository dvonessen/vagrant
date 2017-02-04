# -*- mode: ruby -*-
# vi: set ft=ruby :

suffix='dev01'
fqdn='local'

Vagrant.configure("2") do |config|

  # User debian/contrig-jessie64 Template
  config.vm.box = "debian/contrib-jessie64"

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

      # Provision of Linux Gui with ansible
      config.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible/gui/main.yaml"
        ansible.verbose = "v"
      end
    end
  end

  config.vm.define "server" do |server|
    config.vm.provider "virtualbox" do |v|
      # Set hostname for vm
      config.vm.hostname = "#{suffix}-server.#{fqdn}"
      # Set VM name
      v.name = "#{suffix}-server.#{fqdn}"
      # Display the VirtualBox GUI when booting the machine
      v.gui = false
      # Customize the amount of memory on the VM:
      v.memory = "2048"

      # Provision of Linux Gui with ansible
      config.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible/server/main.yaml"
        ansible.verbose = "v"
      end
    end
  end
end
