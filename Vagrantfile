# Use a virtual machine with all Bob requirements preinstalled
# See https://bob-build-tool.readthedocs.io/en/latest/installation.html#dependencies
# bash, coreutils, tar, hexdump, curl, git, 7z, ...
# Use ubuntu2310 for glibc > 2.36 (for bob basement layer)

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2310"

  # share the project repositoy with the virtual machine
  # mounted at /vagrant
  config.vm.synced_folder ".", "/vagrant"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "bob.embedded.systems"
    
    # increase the amount of memory and cpu
    vb.memory = "8192"
    vb.cpus = 4

    # see https://stackoverflow.com/questions/18457306/how-to-enable-internet-access-inside-vagrant
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
  end

  # provision box with bob
  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    # update packages
    sudo apt-get update
    sudo apt-get -y upgrade

    # install python
    sudo apt-get install -y python3-pip

    # install bob
    sudo python3 -m pip install BobBuildTool --break-system-packages

    # extra dependencies
    sudo apt install -y m4 swig libssl-dev uuid-dev libgnutls28-dev

    # setup project to build in home directory (not in shared folder)
    bob init /vagrant /home/vagrant
  SHELL
end
