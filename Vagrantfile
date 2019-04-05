Vagrant.configure("2") do |config|
    config.vm.box = "sbeliakou/centos"
    config.vm.define "machine" do |machine|
      machine.vm.hostname = "slave-node-3"
      machine.vm.network "private_network", ip: "192.168.56.23"
      machine.ssh.insert_key = false
      config.vm.provider "virtualbox" do |vb|
        vb.name = "machine"
        vb.customize ["modifyvm", :id, "--cpuexecutioncap", "30"]
        vb.memory = "2048"
      end
      machine.vm.provision :ansible do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.inventory_path = "./inventory"
      ansible.limit = "all"
      end
      end
end
