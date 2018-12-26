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
    aws.access_key_id = ""

    # aws.secret_access_key = "YOUR SECRET KEY"
    aws.secret_access_key = ""

    # aws.keypair_name = "KEYPAIR NAME"
    aws.keypair_name = "ak-20181226-us-west-2"

    aws.instance_type = "t2.micro”
    aws.region = 'us-east-1'
    # dcos-ami-1538076223 - ami-0000b5f5376a6a4f1 - centos/7.4/aws/DCOS-1.11.3/docker-18.03.1-ce/selinux_disabled
    # Ubuntu Server 18.04 LTS (HVM), SSD Volume Type - ami-0bbe6b35405ecebdb (64-bit x86) 
    aws.ami = 'ami-0bbe6b35405ecebdb'           # Ubuntu Server 18.04 LTS (HVM) ## Working !!! ##
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
