
Vagrant.configure("2") do |config|

  config.vm.box = "generic/ubuntu2004"
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
  end
  # config.vm.network "public_network", :adapter=>2, type: "dhcp", :bridge => 'wlp1s0'
  config.vm.network "public_network", :adapter=>2, type: "dhcp", :bridge => 'wlp1s0'

  # config.disksize.size = '20GB'

  config.vm.define "webserver" do |machine|
    # machine.vm.network "private_network", ip: "192.168.1.180"
    # machine.vm.network "forwarded_port", guest: 80, host: 8080
    machine.vm.hostname = "webserver"
  end

  config.vm.define "sqlserver" do |machine|
    # machine.vm.network "private_network", :adapter=>2, :bridge => 'wlp1s0', ip: "192.168.16.181"
    machine.vm.hostname = "sqlserver"
  end

  config.vm.define "backupserver" do |machine|
    # machine.vm.network "private_network", :adapter=>2, :bridge => 'wlp1s0', ip: "192.168.16.182"
    machine.vm.hostname = "backupserver"
  end

  config.vm.define "prometheusserver" do |machine|
    # machine.vm.network "private_network", :adapter=>2, :bridge => 'wlp1s0', ip: "192.168.16.170"
    # machine.vm.network "forwarded_port", guest: 10000, host: 8085
    machine.vm.hostname = "prometheusserver"
  end

  # config.vm.provision "shell",
  #   run: "always",
  #   inline: "route add default gw 192.168.16.1"

  # config.vm.provision "shell",    
  #   run: "always",    
  #   inline: "eval `route -n | awk '{ if ($8 ==\"eth0\" && $2 != \"0.0.0.0\") print \"route del default gw \" $2; }'`"

  config.vm.provision "ansible" do |ansible|
  # config.vm.provision "ansible_local" do |ansible|
  # https://www.vagrantup.com/docs/provisioning/ansible_local
    ansible.playbook = "playbooks/init/activate.yml"
    ansible.groups = {
      "apacheservers" => ["webserver"],
      "mysqlservers" => ["sqlserver"],
      "backupservers" => ["backupserver"],
      "prometheusservers" => ["prometheusserver"] 
    }
  end
end
