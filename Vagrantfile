Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.hostname = "blockchainapi"

  config.vm.provider :virtualbox do |vb|
    vb.name = "blockchainapi"
  end

  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network :private_network, ip: "192.168.1.12"
  config.vm.synced_folder ".", "/vagrant", type: "rsync"
  
  config.vm.define "blockchainapi" do |blockchainapi|
  end
  
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "provisionning/bootstrap.yml"
    ansible.inventory_path = "provisionning/inventories/local/hosts"
  end
  
end

