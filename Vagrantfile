Vagrant.configure("2") do |config|
  config.vm.box = "rockylinux/8"
  config.vbguest.auto_update = true
  config.vbguest.installer_options = { allow_kernel_upgrade: true }
  config.vm.provider :virtualbox do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end
  config.vm.provision "shell", inline: "sudo yum install git -y && git clone https://github.com/shendig/ansible-lab.git"
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible-labs/playbooks/vagrant/playbook.yml"
    ansible.verbose  = true
    ansible.inventory_path = "ansible-labs/playbooks/inventory/inventory"
  end
  # Ansible server
  config.vm.define "iac" do |iac|
    iac.vm.hostname = "iac"
    iac.vm.network :private_network, ip: "192.168.3.4"
    iac.vm.provision "shell", inline: "sudo yum update -y && sudo yum install ansible-core tmux -y"
    iac.vm.synced_folder "./vagrant/ansible", "/vagrant"
  end
  # Node1 server
  config.vm.define "node1" do |node1|
    node1.vm.hostname = "node1"
    node1.vm.network :private_network, ip: "192.168.3.5"
    node1.vm.synced_folder "./vagrant/node1", "/vagrant"
  end
  # Node2 server
  config.vm.define "node2" do |node2|
    node2.vm.hostname = "node2"
    node2.vm.network :private_network, ip: "192.168.3.6"
    node2.vm.synced_folder "./vagrant/node2", "/vagrant"
  end
end