# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant::Config.run do |config|

    config.vm.define :web33 do |web_config_33|
        web_config_33.vm.box = "web33"
        web_config_33.vm.box = "precise64"
        web_config_33.vm.box_url = "http://files.vagrantup.com/precise64.box"
        web_config_33.vm.network :hostonly, "33.33.33.100" # Host-Only networking required for nfs shares
        web_config_33.vm.share_folder("symfony", "/vagrant/www", "./www33", :nfs => (RUBY_PLATFORM =~ /linux/ or RUBY_PLATFORM =~ /darwin/))
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
        web_config_44.vm.network :hostonly, "44.44.44.100" # Host-Only networking required for nfs shares
        web_config_44.vm.share_folder("symfony", "/vagrant/www", "./www44", :nfs => (RUBY_PLATFORM =~ /linux/ or RUBY_PLATFORM =~ /darwin/))
        web_config_44.vm.provision :puppet do |puppet|
            puppet.manifests_path = "puppet/manifests"
            puppet.module_path = "puppet/modules"
            puppet.options = ['--verbose']
        end
    end

end

Vagrant.configure("2") do |config|
    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", 4096, "--cpus", "2"]
    end
end