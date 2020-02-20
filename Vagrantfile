# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
config.vm.provision "shell", path: "backup_script.sh"

config.vm.define "box1" do |box1|
box1.vm.box="ubuntu/trusty64"
#box1.vm.provision "shell", inline: <<-SHELL
#sudo apt-get update
#SHELL
box1.vm.network :forwarded_port, guest: 22, host: 10122, id: "ssh"
box1.vm.network :private_network, ip: "192.168.56.101"
box1.vm.provider :virtualbox do |v| 
v.customize ["modifyvm", :id, "--memory", 1020]
end
end

config.vm.define "box2" do |box2|
#box2.vm.provision "shell", inline: <<-SHELL
#sudo apt-get update
#sudo apt-get install -y nginx
#SHELL
box2.vm.box="ubuntu/xenial64" 
box2.vm.network :forwarded_port, guest: 22, host: 10123, id: "ssh"
box2.vm.network :private_network, ip: "192.168.56.102"
end

config.vm.define "box3" do |box3|
box3.vm.provision "shell", inline: <<-SHELL
sudo apt-get update
sudo apt-get install -y apache2
SHELL
box3.vm.box="ubuntu/xenial64" 
box3.vm.network :forwarded_port, guest: 22, host: 10124, id: "ssh"
box3.vm.network :private_network, ip: "192.168.56.103"
end
end