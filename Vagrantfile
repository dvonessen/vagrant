# -*- mode: ruby -*-
# vi: set ft=ruby :

hostname='dev01.local'

Vagrant.configure("2") do |config|
  config.vm.box = "debian/contrib-jessie64"
  config.vm.hostname = "#{hostname}"

  #config.vm.synced_folder "/home/thielking", "/home/thielking"

  config.vm.provider "virtualbox" do |vb|
    # Set VM name
    vb.name = "#{hostname}"
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
    # Enable 3D Acceleration
    vb.customize ["modifyvm", :id, "--accelerate3d",  "on"]
    # Set Video Memory to 128MB
    vb.customize ["modifyvm", :id, "--vram", "128"]
  end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/install.yaml"
  end

  # Reboot Environment
end
