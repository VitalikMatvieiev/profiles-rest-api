# -*- mode: ruby -*-
# vi: set ft=ruby :

# start:

# 1. Open Parallels app
# 2. In folder type: vagrant up --provider parallels
# 3. vagrant ssh

# ref: https://app.vagrantup.com/jeffnoxon/boxes/ubuntu-20.04-arm64

Vagrant.configure("2") do |config|
  config.vm.box = "jeffnoxon/ubuntu-20.04-arm64"

  #config.vm.network "forwarded_port", guest: 8000, host: 8001
  #config.vm.network :private_network, ip: "172.16.101.64"

  config.vm.provision "shell", inline: <<-SHELL
    systemctl disable apt-daily.service
    systemctl disable apt-daily.timer

    sudo apt-get update
    sudo apt-get install -y python3-venv zip
    touch /home/vagrant/.bash_aliases

    if ! grep -q PYTHON_ALIAS_ADDED /home/vagrant/.bash_aliases; then
      echo "# PYTHON_ALIAS_ADDED" >> /home/vagrant/.bash_aliases
      echo "alias python='python3'" >> /home/vagrant/.bash_aliases
    fi
  SHELL
end
