# Infra As A Code Demo

Provision a new VM via IaC, and deploy a webserver
via SCM tool
### Write Infrastructure-as-code and configuration-as-code recipes (using your preferred orchestration software) to:
- Create the server (can be AWS or Azure based)
- Configure an OS image (your choice) appropriately.
- Deploy Nginx webserver.
- Make the Nginx webserver available on port 80.
- Ensure that the server is locked down and secure.

### Provide documentation:
- Instructions for the reviewer which explain how your code should beexecuted
- Requirements for running. (Azure account? Base images? Other tooling pre-installed?)
- Explanation of assumptions and design choices.

Test can be submitted via Github, Public Repo URL

## Pre-requisites
To test this demo, you need to follow below items.

### 1. Vagrant Installation
[Download](https://www.vagrantup.com/downloads.html) and install vagrant for on your host/workstation. (Your laptop or a control server)

Refer [Vagrant Documentation](https://www.vagrantup.com/docs/installation/) as well.

### 2. Plugin Installation - vagrant-aws
Vagrant has default support for VirtualBox, Hyper-V, and Docker. If you want to create your virtual machine on any other environment (like AWS or Azure) still Vagrant has the ability to manage this but only by using  providers plugins. For this case we are using aws and we use **vagrant-aws** plugin.
You may refer [vagrant-aws](https://github.com/mitchellh/vagrant-aws) in github for the same.

```
$ sudo vagrant plugin install vagrant-aws
Installing the 'vagrant-aws' plugin. This can take a few minutes...
Installed the plugin 'vagrant-aws (0.7.2)'!
```

If any issues during installation, install dependencies. (Depends on the workstation machine you are usuing)
```
yum -y install gcc ruby-devel rubygems compass
```

#### Notes
For other providers, you can find and install respective plugins; eg:
```
vagrant plugin install vagrant-digitalocean 
vagrant plugin install vagrant-omnibus
```

### 3. Setup Provider Environment - AWS
- Make sure you have a proper security group created in your VPC (under your AWS account) with SSH, HTTP/HTTPS allowed.
- Make sure you have created a keypair for this purpose and key file (.pem format) has been kept at a secure location on your machine.
- 

#### Box Image 
In normal case with VirtualBox or HyberV, we need to give proper box details to load the image (like a template or clone). But in this case we are using AWS AMI (Amazon Machine Images) and config.vm.box is just for a vagrant syntax purpose. 

You can either add a dummy box(``` vagrant box add aws-dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box ```) or just use any available box image, just like what I did in Vagrantfile.

(You can choose any box by searching [here](https://app.vagrantup.com/boxes/search?provider=aws) for working with VirtualBox, Hyper-V or Docker)
