Vagrant.configure("2") do |config|

  (1..5).each do |i|
    config.vm.define "node-#{i}" do |node|
      node.vm.box = "debian/contrib-buster64"
      node.vm.network "private_network", ip: "192.168.99.10#{i}", auto_config: false

      node.vm.provision "shell", path: "setup", args: "test"

      node.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      end
    end
  end
  
end
