# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.hostname = "ubuntu-ja-cookbook"
  config.vm.box = "chef/ubuntu-13.10"
  config.vm.network :private_network, ip: "192.168.33.15"
  config.vm.provider :virtualbox do |vb|
    vb.gui = false
    vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.name = 'ubuntu-ja-cookbook'
  end
  config.omnibus.chef_version = :latest
  config.vm.provision :chef_solo do |chef|
    chef.json = {
      :mysql => {
        :server_root_password => 'rootpass',
        :server_debian_password => 'debpass',
        :server_repl_password => 'replpass'
      }
    }

    chef.run_list = [
        "recipe[ubuntu-ja-cookbook::default]"
    ]
  end
end
