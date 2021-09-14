#Usage


### 1. Först måste desse instaleras 
```sh 
sudo apt update && sudo apt install ansible virtualbox vagrant
vagrant plugin install vagrant-disksize
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


### 3. För att ssh:a in på maskinerna är det smidigast att köra
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

### 4. Extra info
* Inventory: .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory