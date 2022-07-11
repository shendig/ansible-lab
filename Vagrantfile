Vagrant.configure("2") do |config|
  # Ansible server 1.
  config.vm.define "ansible" do |ansible|
    ansible.vm.hostname = "ansible"
    ansible.vm.network :private_network, ip: "192.168.3.4"
    ansible.vm.box = "rockylinux/8"
    ansible.vm.provider :virtualbox do |ans|
      ans.memory = 2048
      ans.cpus = 2
    end
    ansible.vm.provision "shell", inline: "sudo yum update -y && sudo yum install ansible-core tmux -y"
    ansible.vm.synced_folder "./vagrant/ansible", "/vagrant", disabled: true
  end
  # Node1 server.
  config.vm.define "node1" do |node1|
    node1.vm.hostname = "node1"
    node1.vm.network :private_network, ip: "192.168.3.5"
    node1.vm.box = "rockylinux/8"
    node1.vm.provider :virtualbox do |n1|
      n1.memory = 2048
      n1.cpus = 2
    end
    node1.vm.synced_folder "./vagrant/node1", "/vagrant", disabled: true
  end
  # Node2 server.
  config.vm.define "node2" do |node2|
    node2.vm.hostname = "node2"
    node2.vm.network :private_network, ip: "192.168.3.6"
    node2.vm.box = "rockylinux/8"
    node2.vm.provider :virtualbox do |n2|
      n2.memory = 2048
      n2.cpus = 2
    end
    node2.vm.synced_folder "./vagrant/node2", "/vagrant", disabled: true
  end
end   