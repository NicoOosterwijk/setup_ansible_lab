# Configuration
CLUSTER_SIZE=2

Vagrant.configure("2") do |config|

    required_plugins = %w( vagrant-hostmanager )
    required_plugins.each do |plugin|
      system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
    end

    config.vm.box = "ubuntu/xenial64"
    config.vm.box_version = "20171212.0.0"

    config.vm.define "k8s-master" do |master|
    config.hostmanager.enabled = true
    config.hostmanager.manage_host = false
    config.hostmanager.manage_guest = true
        master.vm.hostname = "k8s-master"
        master.vm.network "private_network", ip: "10.240.0.20"
    end

    (1..CLUSTER_SIZE).each do |i|
        config.vm.define "node#{i}" do |node|
        config.hostmanager.enabled = true
        config.hostmanager.manage_host = false
        config.hostmanager.manage_guest = true
            node.vm.hostname = "node#{i}"
            node.vm.network "private_network", ip: "10.240.0.#{i + 20}"
        end
    end

    config.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.inventory_path = "provisioning/inventory"
      ansible.playbook = "provisioning/playbook.yml"
      ansible.become = true
    end

    config.vm.provision :hostmanager

end
