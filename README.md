# Usage


### 1. Först måste desse instaleras 
```sh 
sudo apt update && sudo apt install ansible virtualbox vagrant
ansible-galaxy install geerlingguy.mysql
ansible-galaxy install mesaguy.prometheus
mkdir /opt/linux1-group1
copy playbooks/init/files/inventory to our opt folder and give it read+write for all
```
Det går även att köra allt på Windows

https://www.vagrantup.com/downloads

https://www.virtualbox.org/wiki/Downloads

https://geekflare.com/ansible-installation-windows/


### 2. Efter det så kör vi detta. Vad det gör är att sätta up två maskiner
```sh
vagrant up
```
Här har nu två maskiner skapats (webserver och sqlserver)


### 3. Run ansible script to setup all the servers
```sh
ansible-playbook main.yml
```


### 4. För att ssh:a in på maskinerna är det smidigast att köra
```sh
vagrant ssh <webserver eller sqlserver>
```
Ni kan också köra 
```sh
vagrant ssh_config >> ~/.ssh/config
```
nu kan ni ssh:a in på maskinerna via vanliga ssh commandot på detta vis
```sh
ssh <webserver eller sqlserver>
```


### 5. Extra info
* Inventory: .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory
