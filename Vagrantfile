# -*- mode: ruby -*-
# vi: set ft=ruby :

#  Require the AWS provider plugin
require 'vagrant-aws'
# Create and configure the AWS instance(s)
Vagrant.configure('2') do |config|
  # config.vm.box = 'dummy'
  config.vm.box = 'perconajayj/centos-x86_64'

  # Specify AWS provider configuration
  config.vm.provider 'aws' do |aws, override|
    # Plugin will read AWS authentication information
    aws.aws_profile = "devops"
    # Specify SSH keypair to use
    aws.keypair_name = 'pe-20181226-us-west-2'
    # instance type
    aws.instance_type = 't2.micro'
    # Specify region, and zone
    aws.region = 'us-west-2'
    # aws.availability_zone = 'us-west-2a'
    # Specify region, AMI ID, and security group(s)
    aws.ami = 'ami-0bbe6b35405ecebdb'           # Ubuntu Server 18.04 LTS (HVM) 
    aws.security_groups = ['secgrp-for-web']
    # Specify username and private key path
    override.ssh.username = 'ubuntu'
    # override.ssh.username = "ec2-user"
    override.ssh.private_key_path = '~/.ssh/pe-20181226-us-west-2.pem'
  end
  
  config.vm.provision "ansible_local" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "deploy-infra.yaml"
  end
end
