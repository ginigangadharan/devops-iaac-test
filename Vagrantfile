# -*- mode: ruby -*-
# vi: set ft=ruby :

require ‘vagrant-aws’

Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"
  config.vm.hostname = "webserver101"
  
  # config.vm.network "forwarded_port", guest: 80, host: 5000
  # config.vm.network "forwarded_port", guest: 5000, host: 80, host_ip: "10.10.10.1"
  
  config.vm.network "private_network", ip: "10.10.10.20"

  # config.vm.network "public_network"
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider ‘aws’ do |aws, override|  
    aws.access_key_id = "YOUR KEY"
    aws.secret_access_key = "YOUR SECRET KEY"
    aws.session_token = "SESSION TOKEN"
    aws.keypair_name = "KEYPAIR NAME"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  # SHELL
  config.vm.provision "ansible_local" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "deploy-infra.yaml"
  end
end
