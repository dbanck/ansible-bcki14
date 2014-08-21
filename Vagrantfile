# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"

  config.vm.define "bcki14" do |node|
    node.vm.provider :lxc do |lxc, override|
      lxc.container_name = :machine

      override.vm.box = "fgrehm/trusty64-lxc"
    end

    node.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "base.yml"
    ansible.groups = {
      "base" => ["bcki14"]
    }
  end
end
