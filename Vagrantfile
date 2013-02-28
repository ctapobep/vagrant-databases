Vagrant::Config.run do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  config.vm.forward_port 3306, 3306

  config.vm.provision :chef_solo do |chef|
    chef.json.merge!({
      :mysql=> {
        :client => { :version => "5.5.28" },
        :server_root_password => "root",
        :server_repl_password => "no_replication",
        :server_debian_password => "root"
      }
    })
    chef.add_recipe("apt-get")
    chef.add_recipe("openssl::default")
    chef.add_recipe("mysql::server")
  end
end
