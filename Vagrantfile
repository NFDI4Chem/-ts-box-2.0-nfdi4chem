# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "tsnfdi4chem" do |tsnfdi4chem|
    tsnfdi4chem.vm.box = "debian/buster64"
    # config.disksize.size = '30GB'
    tsnfdi4chem.ssh.insert_key = false
    tsnfdi4chem.vm.hostname = "tsnfdi4chem.box"
    tsnfdi4chem.vm.synced_folder ".", "/vagrant", create: true, disabled: false
    tsnfdi4chem.vm.network :private_network, ip: "192.168.100.100"

    tsnfdi4chem.vm.provider :virtualbox do |vb|
      vb.name = "tsnfdi4chem_box"
      vb.memory = 4096
      vb.cpus = 2
    end
  end
  config.vm.provision "ansible_local" do |ansible|
    ansible.install = true
    ansible.version = "latest"
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "ansible/playbook.yml"
    ansible.verbose = "true"
    ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
  end
end