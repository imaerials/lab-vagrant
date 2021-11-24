
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-20.04"
  # config.vm.synced_folder "data", "/vagrant"
  config.vm.provision "shell", path: "setup.sh"
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.provision "shell", inline: "echo baz"
  config.vm.provision "ansible_local" do |ansible|
    ansible.install_mode = "pip"
    ansible.inventory_path = "inventory"
    ansible.verbose = "v"
    ansible.become = true
    ansible.playbook = "config.yml"
  end
end
