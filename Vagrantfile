# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "centos65"
  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

  config.vm.network :private_network, ip:"192.168.33.16"
  config.vm.provider :virtualbox do |vb|
    vb.customize ["setextradata", :id, "VBoxInternal/Devices/VMMDev/0/Config/GetHostTimeDisabled", 0]
  end

  config.omnibus.chef_version = :latest
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "./cookbooks"
    chef.run_list = [
      'recipe[yum-pkg]'
    ]
    chef.add_recipe 'yum'
    chef.add_recipe 'build-essential'
    chef.add_recipe 'ruby_build'
    chef.add_recipe 'rbenv::system'
    chef.add_recipe 'git'
    chef.add_recipe 'vim'
    chef.add_recipe 'nginx'
    chef.add_recipe 'unicorn'
    chef.add_recipe 'mongodb'
    chef.add_recipe 'nodejs'
    chef.json = {
      "rbenv" => {
        "global" => "2.1.2",
        "rubies" => [ "2.1.2" ],
        "gems" => {
          "2.1.2" => [
            { 'name' => 'bundler' }
          ]
        }
      }
    }
  end

end
