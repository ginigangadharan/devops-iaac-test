# -*- mode: ruby -*-
# vi: set ft=ruby :

# Require the AWS provider plugin
require 'vagrant-aws'


# Create and configure the AWS instance(s)
Vagrant.configure('2') do |config|
 
  # config.vm.box = 'dummy'
  config.vm.box = 'perconajayj/centos-x86_64'
  # config.vm.hostname = "webserver101"

  # Specify AWS provider configuration
  config.vm.provider 'aws' do |aws, override|
    # Read AWS authentication information from environment variables
    # aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    # aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    # or provide it directly here
    aws.access_key_id = 'AKIAJLKSBHIU7CT76O5Q'
    aws.secret_access_key = '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'
    # Specify SSH keypair to use
    aws.keypair_name = 'ak-20181226-us-west-2'
    # instance type
    aws.instance_type = 't2.micro'
    # Specify region, and zone
    aws.region = 'us-west-2'
    # aws.availability_zone = 'us-west-2a'
    # Specify region, AMI ID, and security group(s)
    # Amazon Linux AMI 2018.03.0 (HVM), SSD Volume Type - ami-01e24be29428c15b2
    # aws.ami = 'ami-01e24be29428c15b2'
    aws.ami = 'ami-0bbe6b35405ecebdb'           # Ubuntu Server 18.04 LTS (HVM) ## Working !!! ##
    aws.security_groups = ['secgrp-for-web']
    # Specify username and private key path
    override.ssh.username = 'ubuntu'
    # override.ssh.username = "ec2-user"
    override.ssh.private_key_path = '~/.ssh/ak-20181226-us-west-2.pem'
  end
  config.vm.provision "ansible_local" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "deploy-infra.yaml"
  end
end
