# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
ENV["LC_ALL"] = "en_US.UTF-8"

Vagrant.configure("2") do |devbox|

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  devbox.vm.box = "pezhore/Ubuntu-17.04-Server"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  devbox.vm.synced_folder "source", "/home/vagrant/source"
  devbox.vm.synced_folder ".", "/vagrant"

  devbox.vm.network "forwarded_port", guest: 5000, host: 5000
  
  # Uncomment this block if you want to fire up a GUI for workstation
  devbox.vm.provider "vmware_workstation" do |v|
    v.gui = true
  end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  #devbox.vm.provision "shell", inline: <<-SHELL
  #  apt-get update
  #  apt-get install -y tmux
  #  wget https://gist.githubusercontent.com/pezhore/23a8fa5174f59c7b56d70ff7cf02c372/raw/0c8f91c61ec386a636599f795c9408b6720b9e02/.tmux.conf
  #SHELL
  devbox.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.verbose  = true
    ansible.install  = true
    ansible.limit    = "all"
  end

  devbox.vm.provision "shell", inline: <<-SHELL
    cd /vagrant && PYTHONUNBUFFERED=1 ANSIBLE_FORCE_COLOR=true ansible-playbook --inventory-file=/tmp/vagrant-ansible/inventory ansible/playbook.yml
  
  SHELL
end
