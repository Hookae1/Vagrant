# -*- mode: ruby -*-
# vi: set ft=ruby :

$update = <<~UPDATE
  echo "LOOKING FOR AN UPDATES"
  apt-get update
  echo "INSTALLING UPDATES"
  apt-get -y upgrade
UPDATE

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.disk :disk, size: "30GB", primary: true
  config.vm.provider "virtualbox" do |vb|
    vb.name = "VVM_1"
    vb.memory = "2048"
    vb.cpus = 2
  end
  config.vm.provision "update", type: 'shell', inline: $update, run: "always"
end
