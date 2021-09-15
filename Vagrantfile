
Vagrant.configure("2") do |config|

  config.vm.box = "generic/ubuntu2004"
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
  end

  # config.disksize.size = '20GB'

  config.vm.define "webserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.21"
    machine.vm.network "forwarded_port", guest: 80, host: 8080
    machine.vm.hostname = "webserver"
  end

  config.vm.define "sqlserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.22"
    machine.vm.hostname = "sqlserver"
  end

  config.vm.define "backupserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.23"
    machine.vm.hostname = "backupserver"
  end

  config.vm.define "prometheusserver" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.24"
    machine.vm.network "forwarded_port", guest: 10000, host: 8085
    machine.vm.hostname = "prometheusserver"
  end

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
