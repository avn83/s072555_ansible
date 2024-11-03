# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.provider "vmware_desktop" do |vw|
     # vw.gui = true
      vw.memory = "512"
  end

    config.vm.define "ubuntu" do |ubuntu|
      ubuntu.vm.box = "bento/ubuntu-20.04-arm64"
      ubuntu.vm.hostname = "ubuntu"
      ubuntu.vm.network "private_network", ip: "192.168.50.4"
      ubuntu.vm.synced_folder "./","/home/vagrant/ansible"
      ubuntu.vm.provision "shell", inline: <<-SHELL
        sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/#g' /etc/ssh/sshd_config
        service ssh restart
        apt update
        apt install -y ansible python3-pip
        pip3 install --upgrade ansible
      SHELL
    end

    config.vm.define "centos" do |centos|
    centos.vm.box = "shk/centos-stream-9-arm64"
    centos.vm.hostname = "centos"
    centos.vm.network "private_network", ip:"192.168.50.5"
    centos.vm.synced_folder "./","/home/vagrant/ansible"
    centos.vm.provision "shell", inline: <<-SHELL
      yum install -y epel-release
      yum install -y ansible
    SHELL
  end

end
