# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define :web33 do |web_config_33|
            web_config_33.vm.box = "web33"
            web_config_33.vm.box = "precise64"
            web_config_33.vm.box_url = "http://files.vagrantup.com/precise64.box"
            web_config_33.vm.network "private_network", ip: "33.33.33.100"
            web_config_33.vm.synced_folder ".", "/vagrant", type: "nfs", disabled: true
            web_config_33.vm.synced_folder "./www33", "/vagrant/www", type: "nfs"
            web_config_33.vm.provision :puppet do |puppet|
                puppet.manifests_path = "puppet/manifests"
                puppet.module_path = "puppet/modules"
                puppet.options = ['--verbose']
            end
    end
    config.vm.define :web44 do |web_config_44|
            web_config_44.vm.box = "web44"
            web_config_44.vm.box = "precise64"
            web_config_44.vm.box_url = "http://files.vagrantup.com/precise64.box"
            web_config_44.vm.network "private_network", ip: "44.44.44.100"
            web_config_44.vm.synced_folder "./www44", "/vagrant/www", type: "nfs"
            web_config_44.vm.provision :puppet do |puppet|
                puppet.manifests_path = "puppet/manifests"
                puppet.module_path = "puppet/modules"
                puppet.options = ['--verbose']
            end
    end
end