# -*- mode: ruby -*-
# vi: set ft=ruby :

#-----------------------------------------------------------------------------------------------------------------#
#
# @Autor : Kenneth Dzonyrah
# Description : Vagrant file and script for provisionning Jenkins installation
# Date : 03/22/2022
#
#------------------------------------------------------------------------------------------------------------------#

Vagrant.configure("2") do |config|
  # jenkinshost-ken : is the name that have our server
  config.vm.define "install-jenkins-maven" do |jenkinshost|
    jenkinshost.vm.box = "centos/7"
    jenkinshost.vm.hostname = "install-jenkins-maven"
    jenkinshost.vm.network "private_network", ip: "192.168.55.147"      
    #jenkinshost.vm.box_url = "utrains/centos7"
    jenkinshost.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--name", "install-jenkins-Maven"]
      v.customize ["modifyvm", :id, "--cpus", "2"]
    end
    config.vm.provision "shell", inline: <<-SHELL
      sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
      sudo systemctl restart sshd
    SHELL
    #install_jenkinshost.sh : This is the script that will take care of the installation of Java, Jenkins server and some utilities
    jenkinshost.vm.provision "shell", path: "install_jenkins.sh"
  end
end
