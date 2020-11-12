# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.network "forwarded_port", guest: 3000, host: 3000, host_ip: "127.0.0.1"
    config.vm.network "forwarded_port", guest: 27017, host: 27017, host_ip: "127.0.0.1"
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "2096"
    end
    config.vm.provision "shell", inline: <<-SHELL
      # Install the bb-hub(&video) dependencies
      apt-get update
      # Install the docker environment
      apt-get install -y docker.io docker-compose
      usermod -aG docker vagrant
      # Create the a 2GB swap file
      touch /var/swap.img
      chmod 600 /var/swap.img
      dd if=/dev/zero of=/var/swap.img bs=1024k count=2000
      mkswap /var/swap.img
      swapon /var/swap.img
      echo "/var/swap.img    none    swap    sw    0    0" >> /etc/fstab
      systemctl enable docker
      # Create the MongoDB volume
      docker volume create mongodb
      cd /vagrant && docker-compose up -d
      # Install MongoDB client and tools
      wget -qO - https://www.mongodb.org/static/pgp/server-4.0.asc | apt-key add -
      echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.0.list
      apt-get update
      apt-get install -y mongodb-org-shell=4.0.9 mongodb-org-tools=4.0.9
    SHELL
  end
  