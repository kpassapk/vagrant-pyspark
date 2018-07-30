# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.define "pyspark-box"
  # Forward ssh keys from host to guest
  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
  end

  # Share Jupyter Notebook's port with the outside world
  config.vm.network "forwarded_port", guest: 8888, host: 8888

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.verbose = 'v'
    ansible.extra_vars = {
      ansible_python_interpreter: "/usr/bin/python3",
    }
  end

  config.vm.synced_folder "/Users/kyle/src/org/bitbucket/kpassapk/cs38-fall18-projects", "/projects"
end
