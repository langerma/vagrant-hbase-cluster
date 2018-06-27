# vagrant-hbase-cluster
test ansible playbooks and basic functionality

## init
```sh
git clone https://github.com/langerma/vagrant-hbase-cluster
cd vagrant-hbase-cluster
git submodule init
git submodule update
vagrant up
ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory prepare.yml
```

## install zookeeper
```sh
ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory zookeeper.yml
```

## install and bootstrap hdfs
```sh
ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory hdfs.yml
```

## install hbase
```sh
ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory hbase.yml
```

## upgrading
```sh
cd vagrant-hbase-cluster
git submodule foreach git pull origin master
```
