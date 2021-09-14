
Vagrant.configure("2") do |config|

  config.vm.box = "generic/ubuntu2004"
  # config.disksize.size = '20GB'

  config.vm.define "webserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.21"
    machine.vm.hostname = "web-srv"
  end

  config.vm.define "sqlserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.22"
    machine.vm.hostname = "sql-srv"
  end

  config.vm.define "backupserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.23"
    machine.vm.hostname = "backup-srv"
  end

  config.vm.define "loggingserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.24"
    machine.vm.hostname = "logging-srv"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/init/activate.yml"
    ansible.groups = {
      "http" => ["webserver"],
      "sql" => ["sqlserver"],
      "bak" => ["backupserver"],
      "log" => ["loggingserver"] 
    }
  end


end
