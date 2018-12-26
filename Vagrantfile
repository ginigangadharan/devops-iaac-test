# -*- mode: ruby -*-
# vi: set ft=ruby :

# Require the AWS provider plugin
require 'vagrant-aws'

# Create AWS Instance
Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"
  config.vm.hostname = "webserver101"
  
  # config.vm.network "forwarded_port", guest: 80, host: 5000
  # config.vm.network "forwarded_port", guest: 5000, host: 80, host_ip: "10.10.10.1"
  # config.vm.network "private_network", ip: "10.10.10.20"
  # config.vm.network "public_network"
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider ‘aws’ do |aws, override|  

    # aws.access_key_id = "YOUR KEY"
    aws.access_key_id = "AKIAIL2WFWXVXFTZ65MQ"

    # aws.secret_access_key = "YOUR SECRET KEY"
    aws.secret_access_key = "XcYU660B9q9eumpg3vatgV9K2wldQNr23E3n6EC8"

    # aws.keypair_name = "KEYPAIR NAME"
    aws.keypair_name = "ak-20181226-us-west-2"

    aws.instance_type = "t2.micro”
    aws.region = 'us-east-1'
    aws.ami = 'ami-20be7540'
    aws.security_groups = ['secgrp-for-web']

    override.vm.box = "dummy"
    override.ssh.username = 'devops'
    override.ssh.private_key_path = '~/.ssh/ssh-keypair-file'

  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.verbose = "v"
    #ansible.playbook = "deploy-infra.yaml"
  end
end
