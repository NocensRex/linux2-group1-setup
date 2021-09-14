
Vagrant.configure("2") do |config|

  config.vm.box = "generic/ubuntu2004"

  config.vm.define "webserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.21"
    machine.vm.hostname = "webserver"
  end

  config.vm.define "sqlserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.22"
    machine.vm.hostname = "sqlserver"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/activate.yml"
    ansible.groups = {
      "http" => ["webserver"],
      "sql" => ["sqlserver"]
    }
  end


end
